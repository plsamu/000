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



|    | 00 |
| -- | -- |
| 1  | 01 |
| 2  | 02 |
| 3  | 03 |
| 4  | 04 |
| 5  | 05 |
| 6  | 06 |
| 7  | 07 |
| 8  | 08 |
| 9  | 09 |
| 10 | 0A |
| 11 | 0B |
| 12 | 0C |
| 13 | 0D |
| 14 | 0E |
| 15 | 0F |

```
5AFE...
FADE...

```
