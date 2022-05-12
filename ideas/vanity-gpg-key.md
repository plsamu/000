# Vanity GPG Key

* [Basic "theory"](../ict/gpg-key.md)

## Automate it --- AKA less security and more implementation difficulties

{% hint style="warning" %}
It is likely that you are running out of entropy. \
\
Key generation requires a lot of very high-quality random numbers; without the activity of the user to provide high-quality randomness to the computer, the entropy pool is being exhausted by generation, and the generation process just hangs, waiting for the pool to refill.
{% endhint %}

{% embed url="https://serverfault.com/questions/691120/how-to-generate-gpg-key-without-user-interaction" %}

{% embed url="https://www.gnupg.org/documentation/manuals/gnupg/Unattended-GPG-key-generation.html" %}

## What combinations are possible?

```
0 1 2 3 4 5 6 7 8 9 A B C D E F

5AFE
FADE
```

{% embed url="https://github.com/Diti/EgoKey" %}
