# Nmap

{% embed url="https://nmap.org/man/it/man-briefoptions.html" %}

{% embed url="http://scanme.nmap.org" %}

{% embed url="https://www.reddit.com/r/AskNetsec/comments/a1i3gl/how_do_you_detect_nmap_scans" %}

### There are a lot of flags in this section

{% hint style="warning" %}
Tor nodes are blacklisted and probably blocked
{% endhint %}

{% hint style="success" %}
[Use Tor with random proxies](../roadmap/000-basics-level/explanations/enter-anonymous.md)&#x20;
{% endhint %}

{% hint style="success" %}
If you scan a network, do a random scan flagging already scanned IPs
{% endhint %}

{% hint style="success" %}
Slow scan ad libitum
{% endhint %}

## Questions

<details>

<summary>Why nmap?</summary>

cuz is massive, extensible, well documented and widely used

</details>

<details>

<summary>Why port scanning?</summary>

Try scan your default gateway and see what you find.

```
nmap -vv -A 192.168.1.1
```

</details>

## Where to start

{% embed url="https://nmap.org/nsedoc/categories" %}

