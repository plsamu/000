# RSA

```bash
# generate keypair, PKCS#1
openssl genrsa -out keypair.pem 4096

# read file created
cat keypair.pem

# extract pub key, that is already in PKCS#8
openssl rsa -in keypair.pem -pubout -out pub.pkcs8

# export keypair to standard PKCS#8
openssl pkcs8 -topk8 -inform PEM -outform PEM -nocrypt -in keypair.pem -out pri.pkcs8

# export keipair to standard PKCS#12 (.pfx, .p12)
openssl pkcs12 -export -out pair.pfx -inkey keypair.pem -in pub.pkcs8
```

### Try your keys

`reccomended: RSA/ECB/OAEPWithSHA-1AndMGF1Padding`

{% embed url="https://www.devglan.com/online-tools/rsa-encryption-decryption" %}

### Example

* [android-rsa.md](../../../dev/mobile-dev/android/encrypt-a-string-with-private-key/android-rsa.md "mention")
