# RSA

```bash
# generate keypair
openssl genrsa -out keypair.pem 4096

# read file created
cat keypair.pem

# extract pub key
openssl rsa -in keypair.pem -pubout -out publickey.crt

# export keypair to standard PKCS#8
openssl pkcs8 -topk8 -inform PEM -outform PEM -nocrypt -in keypair.pem -out pkcs8.key

# export keipair to standard PKCS#12
openssl pkcs12 -export -out public_privatekey.pfx -inkey keypair.pem -in publickey.crt
```

