# EC

As RSA had different key sizes (512, 1024, 2048, 4096).&#x20;

As ECC has different curves.

## FAQ

<details>

<summary>Do Android support EC encryption decryption?</summary>

Nope. You have to use RSA keys.\
EC in Android should be available only for sign operation and not encryption/decryption...

[https://stackoverflow.com/questions/57087599/how-to-encrypt-and-decrypt-data-in-android-using-the-elliptic-curve-key-pair-of](https://stackoverflow.com/questions/57087599/how-to-encrypt-and-decrypt-data-in-android-using-the-elliptic-curve-key-pair-of)

</details>

### list curves

```
openssl ecparam -list_curves
```

Some shit:

* secp521r1 (P-521)
* sect571r1
* c2tnb431r1
* brainpoolP512t1

{% embed url="https://malware.news/t/everyone-loves-curves-but-which-elliptic-curve-is-the-most-popular/17657" %}

### Generate ECC Key

#### method 1

```
openssl ecparam -name secp521r1 -genkey -out privkey.ec
```

```
-----BEGIN EC PARAMETERS-----                                                                 │
BgUrgQQAIw==                                                                                  │
-----END EC PARAMETERS-----                                                                   │
-----BEGIN EC PRIVATE KEY-----                                                                │
MIHcAgEBBEIBZymJijpTa84ubogvKbLaCYF95DbvG4wDqKiWMz/HenaXZmnLxh6c                              │
d3mKii2wRHCsF2bAGFrbguPJ8YH69DRk3E2gBwYFK4EEACOhgYkDgYYABABpMcoT                              │
poWOACXFP01zssUolh7NAwftWc90qROEIJ9CzKhVCdxtL5+wITK5FGtxR1wmsHxk                              │
GoMj3LoFTrUbBrAaJgEn5z17DA++HmxzBh3ImVc86W2QeOAU8v2znUY/y+XURVhe                              │
lmMmOHiroDlL1S2HrINa7A5yCmkiaOhykY7s/3uK7A==                                                  │
-----END EC PRIVATE KEY-----  
```

#### method 2

```
openssl ecparam -name secp521r1 -genkey -noout -out privkey.ec
```

```
-----BEGIN EC PRIVATE KEY-----                                                                │
MIHcAgEBBEIBD61P1NVt/JdlzKSPSS1lS8wgaNtgdsmofWf/do5eI93/+pH/d7CO                              │
zxveItL3oXkw17+urrrSD+zRquOvv4IuqoigBwYFK4EEACOhgYkDgYYABAFikDKf                              │
7Ipvzuana8gi/c9+dcK1Ud2Xnm4uGsWFCd2mc8ucpr5+3/wSgJ4LIKrWyk4rpKMC                              │
ZYvV+kuNwVrAAw/4BAAn1BNO1+i1x3IrmEuyCxygf7RJgn6AqBgroyYrnkQeMhiC                              │
9xjVJT8ZViPeIhWX5C26/K+zRU0sFiZymqRYKyG6hg==                                                  │
-----END EC PRIVATE KEY-----   
```

### Obtain pub and info of key

```
openssl ec -in priv.ec.key -noout -text
```

### get params

```
openssl ec -in private.ec.key -param_out > params
```

### get pub

```
openssl ec -in private.ec.key -pubout >> pub
# or
openssl ec -in keys.pem -pubout -out pub
```

## Encrypt / Decrypt

{% embed url="https://stackoverflow.com/questions/62155130/openssl-command-for-encryption-decryption-with-prime256v1-private-key" %}

{% embed url="https://superuser.com/questions/1003690/how-can-i-encrypt-a-file-with-an-ec-public-key" %}

```
openssl enc -ciphers
```

{% embed url="https://stackoverflow.com/questions/1220751/how-to-choose-an-aes-encryption-mode-cbc-ecb-ctr-ocb-cfb" %}
