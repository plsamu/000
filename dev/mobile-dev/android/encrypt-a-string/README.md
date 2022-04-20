# Encrypt a string

## Beware

{% embed url="https://stackoverflow.com/questions/57087599/how-to-encrypt-and-decrypt-data-in-android-using-the-elliptic-curve-key-pair-of" %}

## RAW - Do not read here

{% embed url="https://stackoverflow.com/questions/64012929/convert-bytearray-to-privatekey-in-kotlin" %}

### get priv key

```
openssl ecparam -name secp521r1 -genkey -noout -out pri
```

### get pub key

```
openssl ec -in pri -pubout -out pub
```

### load them as raw files

### use them

```kotlin
val dsa = Signature.getInstance("SHA1withECDSA")
try {
    val curveName = "secp521r1"
    val kf = KeyFactory.getInstance("EC")
    val params = AlgorithmParameters.getInstance("EC")
    params.init(ECGenParameterSpec(curveName))
    val spec = params.getParameterSpec(ECParameterSpec::class.java)

    val priRaw = resources.openRawResource(R.raw.pri)
    val priKeyBI = BigInteger(1, priRaw.readBytes())
    val priSpec = ECPrivateKeySpec(priKeyBI, spec)
    val pri = kf.generatePrivate(priSpec)

    val pubRaw = resources.openRawResource(R.raw.pub)
    val pubKeyBI = BigInteger(1, pubRaw.readBytes())
    val pubSpec = ECPublicKeySpec(ECPoint(spec.curve.a, spec.curve.b), spec)
    val pub = kf.generatePublic(pubSpec)

    dsa.initSign(pri)
    dsa.initVerify(pub)
} catch (e: Exception) {
    e.printStackTrace()
}
```
