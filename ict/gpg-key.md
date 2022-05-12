# GPG Key

{% hint style="success" %}
PG is more of a key manager
{% endhint %}

## Generate basic GPG key

```
gpg --gen-key
```

{% hint style="danger" %}
**Anybody having access to your revocation certificate can revoke your key, rendering it useless.**
{% endhint %}



## List all your keys

Keys are in `~/.gnupg`

```bash
gpg --list-keys
# also
gpg --fingerprint
```

{% hint style="success" %}
The fingerprint of a key is used to ensure that you have the right public key.
{% endhint %}

```
SHA-1 hash:               0D69E11F12BDBA077B3726AB4E1F799AA4FF2279
fingerprint:    0D69 E11F 12BD BA07 7B37  26AB 4E1F 799A A4FF 2279  // with double space in the center
long id:                                       4E1F 799A A4FF 2279
short id:                                                A4FF 2279
```



## Where is the public key to publish?

{% hint style="info" %}
Inside the pubring.kbx probably (\~/.gnupg/pubring.kbx)

You have to export it.
{% endhint %}

```
gpg --armor --export your@email.com

--armor
    causes output to be generated in an ASCII-armored format 
    similar to uuencoded documents

--export
     export keys from all keyrings
```

```
-----BEGIN PGP PUBLIC KEY BLOCK-----

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
=W+Gd
-----END PGP PUBLIC KEY BLOCK-----

```

## Should I extract the private key?

{% embed url="https://www.gnupg.org/gph/en/manual/r887.html" %}

> This is normally not very useful and is a security risk since private keys are left unprotected.

```
gpg --export-secret-keys YOUR_ID_HERE
```

## Others

```
sudo apt install gnupg2
```

## Sources

{% embed url="https://help.ubuntu.com/community/GnuPrivacyGuardHowto" %}

{% embed url="https://unix.stackexchange.com/questions/481939/how-to-export-a-gpg-private-key-and-public-key-to-a-file" %}

{% embed url="https://security.stackexchange.com/questions/110139/gnupg-asks-for-a-key-id-when-sharing-my-public-key-what-is-that" %}
