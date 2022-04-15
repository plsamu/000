# Recover .onion url

### save keys

```
cat hs_ed25519_secret_key | base32   # then copy the output
cat hs_ed25519_public_key | base32   # then copy the output
```

(then here to test I deleted all the files: hostname, hs\_ed25519\_secret\_key and hs\_ed25519\_public\_key**)**

### recover hostname

```
echo "HU6SAZLEGI2TKMBLABLABLA====" | base32 -d > hs_ed25519_secret_key
echo "THE_OTHER_BLABLABLABASE32CH" | base32 -d > hs_ed25519_public_key
```

```
systemctl restart tor
```

## FK  THIS

### problem

```
cat hs_ed25519_secret_key

== ed25519v1-secret: type0 ==  Ou���#�G<���䏃tnj�G%�YW�z�K�4�*�/޾ϸ;a�vI��H��Q͝$
```

### get the base64

```
dd if=hs_ed25519_secret_key bs=1 skip=32 | base64
```

### recover

```bash
#!/bin/bash

secret_key_binary_64=$(cat base64_secret_key | base64 -d)
sec_bin_key="== ed25519v1-secret: type0 =="+"$secret_key_binary_64"
echo $sec_bin_key

public_key_bin64=$(cat base64_public_key | base64 -d)
pub_bin_key="== ed25519v1-public: type0 =="+"$public_key_bin64"
echo $pub_bin_key
```

### recover and change the secret key

```
sudo echo "== ed25519v1-secret: type0 ==$(cat base64_secret_key | base64 -d)" > /path/to/service/
```

## method 2

{% hint style="info" %}
should I use base32 or base64 ?
{% endhint %}

### get base32

```
cat hs_ed25519_secret_key | cut -b 32-999 | base32 | xargs -I{} echo"{}" > base32_priv
```

### return to bin

```
cat base32_priv | base32 -d | xargs -I{} echo "== ed25519v1-secret: type0 =={}" > hs_ed25519_secret_key  
```
