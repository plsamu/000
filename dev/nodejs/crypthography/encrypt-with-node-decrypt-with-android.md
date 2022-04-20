# Encrypt with Node, decrypt with Android

{% hint style="warning" %}
Do not do this!

Just use a script in Kotlin if you need to encrypt in `RSA/ECB/OAEPPadding`with `MGF1ParameterSpec`
{% endhint %}

Two way to do this:

* fastest: download IntelliJ IDEA
* download kotlin (kotlinc) and setup vscode

## NodeJS

```javascript
const fs = require('fs')
const crypto = require("crypto")

const data = {
    str1: "somestr"
}

const pri = fs.readFileSync("./keypair.pem", 'utf-8')
const encrypted = crypto.privateEncrypt(pri, Buffer.from(JSON.stringify(data)))
let base64encoded_ciphertext = encrypted.toString("base64")
console.log(base64encoded_ciphertext)
fs.writeFileSync("./ciphertext", base64encoded_ciphertext)
```

{% embed url="https://nodejs.org/api/crypto.html#cryptoprivateencryptprivatekey-buffer" %}

## Android Kotlin

```kotlin
val ciphertext =
    "PTcQ6q3gcdaFXCNVl9M5t5qK4QhyOTm28VNS5DJ/0nvh+zajzLwwxEUADSCm6XUNqTH3/nyFwhnKIQZ3SktgebbBLXxE0kR57auwlKtg36xumCQ7iJoHOMn4emDaywHl92PVq9XCmX6NgXySVopMGNDNKVG4svki6biejGbUyPztDQy9e6DoVactKFrf/hdD7J69ll7iPm+1MzO4M9w4Gam+9OmyxZTA91vY17ZmAC/CbEjCMMSm86bqCnwGQb/AsCRBAQu5LoO7+q4vAzRGyY/HiQDiKQXQ6L3Xz3Oc4MyZuKKjzK74npo2YkQkbblhm+LwVXE6CpnUUPpMdwnx4tdKPOctaC9KdT9ZeYps/ub3zrutkhV/lTVkkrw5zMBgbGBtzHJpU2Rv88FKwm/mDSNqzw4cIDbaYuX+Eg7ixt+cnXJ90Zv1w6gyma8Swnqu0mPlXkOWmXp1djiT0FG1qCU1iLYY691VqKAejcmbSBJiI9B1MxTME/f88ivL6PO+s3x1eE3FFBSw4UrU4AP0BpNicaOQZcJOCikax2UjHSQNMo1ZlczNHjOfAla89mrEFQcrnZ8JcHLTRxAjBE4jka0Z0aTjl+0Lo/cd+OT3fe4IUZahatyMk1FR4BY6Bu65u1e3Et+z3uO92mTJr7ms6OHaPEVN00xiy6CFga0yVCs="
val pubKey = KeyHelper.getPubKeyFromFile(this, R.raw.pub)
val cipher = Cipher.getInstance("RSA/ECB/NoPadding")
cipher.init(
    Cipher.DECRYPT_MODE,
    pubKey
)
val bytes = Base64.decode(ciphertext.encodeToByteArray(), Base64.CRLF)
val text = cipher.doFinal(bytes)
Log.d(TAG, text.decodeToString())
```

