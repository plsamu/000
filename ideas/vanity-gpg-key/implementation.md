# Implementation

## Flow

```
gpg --quick-gen-key --batch --passphrase "" "arctic (my secrets)" default default never
gpg --delete-secret-key arctic     // delete private (secret) in pubring
gpg --delete-key arctic            // delete public
gpg --list-key                     // should be empty
```

## How --quick-gen-key works?

{% embed url="https://www.gnupg.org/documentation/manuals/gnupg/OpenPGP-Key-Management.html" %}

```
gpg --quick-gen-key --batch --passphrase "" {userId}
```

{% hint style="info" %}
A passphrase can be added after the creation!
{% endhint %}





