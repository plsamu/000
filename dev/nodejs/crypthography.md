# Crypthography

```javascript
const fs = require('fs')
const crypto = require("crypto")

const data = "my secret data"
const pri = fs.readFileSync("./pri.pkcs1", 'utf-8')
const encrypted = crypto.privateEncrypt(pri, Buffer.from(data))
console.log("encypted data: ", encrypted.toString("base64"))
```
