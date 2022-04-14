# binary keys to base64

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
