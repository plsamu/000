# Add repositories

{% embed url="https://www.kali.org/docs/general-use/kali-linux-sources-list-repositories" %}

```
sudo nano /etc/apt/sources.list 
    deb-src http://http.kali.org/kali kali-rolling main contrib non-free
    deb http://http.kali.org/kali kali-last-snapshot main contrib non-free

sudo apt update
```
