# Crypthography

### Encrypt with RSA pri key (PKCS#1) from file

[How to generate key](../../../../ict/cryptography/openssl/rsa.md).

```javascript
const fs = require('fs')
const crypto = require("crypto")

const data = "my secret data"
const pri = fs.readFileSync("./keypair.pem", 'utf-8')
const encrypted = crypto.privateEncrypt(pri, Buffer.from(data))
let base64encoded_ciphertext = encrypted.toString("base64")
console.log("ciphertext: ", base64encoded_ciphertext)
```

```
ciphertext: kQYXC8ynd/3/HU6wV5w547hVYB3ecqpmFFxgxA15sF8EWzQeFeDbMLg2bF2AyU1JrKveb4mksQSZBXB2CitLWvJh9u+zD8jOkTOEv21EDTqvMTk8oGGJ0j7DvkCUUuOa/KpFuexlamxz3CJrNdst6IqP69zVfXAE8CNOv0jfOF7zZxmpIGx4t5zWp8ij2GOY4R8MufNHqdFk+DlgmEOvdkREvDgkGK+Uvn8WN+QbrCPlT1B9kGz8NcXU9jgLGCOpnJkOjsi9JPKfjFZdAwi2PlZns3SBMahP7Jfbksm2QBM1C2ot9c/2Gj/FR2y9Hx9r5ImJABVImgFomQe7U1b7237Gt2+HB6gYH91bDJPs/LbMmAMgO3L48hkzH4aTGREuQ6yIJNEgESGHOumvcRgB01d7IdDGNk8fxcOjpq0me4a2Hppx9Tdiw2JVBkYlVA2edAE5Uf1vP1Il97kYGGvscYx2UtvmcFPqRyEt3q+TZ1h8zFHde58VOFu4fjV0u5oTgXrM/F5ge6kkqHa7dRqbhATPAkwoE8Gp/s1HIT+VqGzdbC9t0eZOb49+X6aRkjojx9CXq/0WsjaaDpA3XvQ5i2PZ4R4lBG/OLKjUs2Vc7SBS3ofzDORp6tSwJ5n+ZCJA5ENvEw3aNzIc=
```

### Encrypt JSON

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

### Decrypt

```javascript
const fs = require('fs')
const crypto = require("crypto")

const pub = fs.readFileSync("./pub.pkcs8", 'utf-8')
const ciphertext = fs.readFileSync("./ciphertext", 'utf-8')
const decrypted = crypto.publicDecrypt(pub, Buffer.from(ciphertext, 'base64'))
console.log(decrypted.toString('ascii'))
```

```
my secret data
```
