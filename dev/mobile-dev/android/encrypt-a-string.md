# Encrypt a string

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
    val kf = KeyFactory.getInstance("EC")

    val priRaw = resources.openRawResource(R.raw.pri)
    val priSpec = X509EncodedKeySpec(priRaw.readBytes())
    val pri = kf.generatePrivate(priSpec)

    val pubRaw = resources.openRawResource(R.raw.pub)
    val pubSpec = X509EncodedKeySpec(pubRaw.readBytes())
    val pub = kf.generatePublic(pubSpec)

    dsa.initSign(pri)
    dsa.initVerify(pub)
} catch (e: Exception) {
    e.printStackTrace()
}
```
