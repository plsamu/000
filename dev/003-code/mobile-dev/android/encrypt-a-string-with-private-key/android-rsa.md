# Android RSA

## Theory

OAEP is padding scheme, which needs 2 hash functions with different properties to operate.

* One hash function should map arbitrary sized input to fixed size output. This type of hash functions are well known, `SHA-256`, `MD5` and so on are all of this type. Specification allows different functions to be used for OAEP padding.
* Another hash function should map arbitrary sized input to arbitrary sized output. Such hash function is called "mask generation function" (MGF). The related [RFC](https://www.rfc-editor.org/rfc/rfc8017#appendix-B.2) defines only one such function, MGF1 with sometime only `SHA-1` and sometime also with `SHA-256`.

## Code

### Generate keypair

```bash
openssl genrsa -out keypair.pem 4096

# extract pub key, that is already in PKCS#8
openssl rsa -in keypair.pem -pubout -out pub.pkcs8

# export keypair to standard PKCS#8
openssl pkcs8 -topk8 -inform PEM -outform PEM -nocrypt -in keypair.pem -out pri.pkcs8
```

### PKCS8Helper

```kotlin
class PKCS8Helper {
    companion object {
        fun getPriKeyFromFile(context: Context, id: Int): PrivateKey {
            val kf = KeyFactory.getInstance("RSA")
            val keyBytes = context.resources.openRawResource(id)
            val pri = keyBytes.bufferedReader(Charset.defaultCharset()).lines()
                .collect(Collectors.joining("\n"))
            val priEncodedPart =
                pri
                    .removePrefix("-----BEGIN PRIVATE KEY-----")
                    .removeSuffix("-----END PRIVATE KEY-----")
                    .replace("\n", "")
            val specPKCS8 = PKCS8EncodedKeySpec(Base64.decode(priEncodedPart, Base64.DEFAULT))
            return kf.generatePrivate(specPKCS8)
        }

        /**
         * PKCS8EncodedKeySpec(Base64.decode(pubEncodedPart, Base64.DEFAULT))
         */
        fun getPubKeyFromFile(context: Context, id: Int): PublicKey {
            val kf = KeyFactory.getInstance("RSA")
            val keyBytes = context.resources.openRawResource(id)
            val pub = keyBytes.bufferedReader(Charset.defaultCharset()).lines()
                .collect(Collectors.joining("\n"))
            val pubEncodedPart =
                pub
                    .removePrefix("-----BEGIN PUBLIC KEY-----")
                    .removeSuffix("-----END PUBLIC KEY-----")
                    .replace("\n", "")
            val df = X509EncodedKeySpec(Base64.decode(pubEncodedPart, Base64.DEFAULT))
            return kf.generatePublic(df)
        }
    }
}
```

### How to use

```kotlin
val priKey = PKCS8Helper.getPriKeyFromFile(requireContext(), R.raw.pri)
val pubKey = PKCS8Helper.getPubKeyFromFile(requireContext(), R.raw.pub)

val cipher = Cipher.getInstance("RSA/ECB/OAEPPadding")
var usable: String = ""
btnEnc.setOnClickListener {
    cipher.init(Cipher.ENCRYPT_MODE, priKey, OAEPParameterSpec("SHA-256", "MGF1", MGF1ParameterSpec.SHA256, PSource.PSpecified.DEFAULT))
    val cipherBytes = cipher.doFinal(edit1.text.toString().encodeToByteArray())
    usable =  Base64.encode(cipherBytes, Base64.DEFAULT).decodeToString()
    txt1.text = usable
}

btnDec.setOnClickListener {
    cipher.init(Cipher.DECRYPT_MODE, pubKey, OAEPParameterSpec("SHA-256", "MGF1", MGF1ParameterSpec.SHA256, PSource.PSpecified.DEFAULT))
    val bytes = Base64.decode(usable, Base64.DEFAULT)
    val text = cipher.doFinal(bytes)
    txt2.text = text.decodeToString()
}
```
