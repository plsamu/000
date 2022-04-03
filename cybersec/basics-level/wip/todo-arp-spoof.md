# TODO - ARP spoof

## Overhead

I have 2 devices connected to my LAN via WiFi.\
In one I have installed Kali Linux and I want to read the traffic of the other.

1. Get the IP
2. ARP spoof

## Get the IP

### Advance list scan

```
ip addr

2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    inet 192.168.1.181/24 brd 192.168.1.255 scope global dynamic noprefixroute eth0

```

`192.168.1.181/24`

> Another reason for an advance list scan is stealth. In some cases, you do not want to begin with a full-scale assault on the target network that is likely to trigger IDS alerts and bring unwanted attention. A list scan is unobtrusive and provides information that may be useful in choosing which individual machines to target. It is possible, though highly unlikely, that the target will notice all of the reverse-DNS requests. When that is a concern, you can bounce through anonymous recursive DNS servers using the `--dns-servers` option as described in [the section called “DNS proxying”](https://nmap.org/book/subvert-ids.html#defeating-firewalls-dns-proxy).

```
sudo macchanger -r eth0 
nmap -sL 192.168.1.0/24
```

Feels like this reverse DNS request is pretty broken...\
Not only I know the IP, but also the hostname...

```
Nmap scan report for OnePlus5.blabla.bla (192.168.1.115)
```



## Sources

{% embed url="https://nmap.org/book/host-discovery-controls.html" %}

<details>

<summary>What is a reverse-DNS requests?</summary>

A reverse DNS is a DNS lookup of a domain name from an IP address.

You send and IP and you get the host name.

</details>

<details>

<summary>Can a host be invisible to reverse DNS request?</summary>

Idk but, I found that reverse DNS request can be filtered. This goes to Advance topic hands down.

</details>

<details>

<summary>Who is the DNS resolver?</summary>

```bash
cat /etc/resolv.conf 
# or better
( nmcli dev list || nmcli dev show ) | grep DNS
```

</details>

{% embed url="https://www.youtube.com/playlist?list=PLTgRMOcmRb3PS-l6V_r3gCwKjVRWvCMQa" %}

