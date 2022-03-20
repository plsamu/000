# Became Anonymous

## Proxies, Tor, VPN

{% embed url="https://www.youtube.com/watch?index=17&list=PLYmlEoSHldN7HJapyiQ8kFLUsk_a7EjCw&v=IJt8ThZlGGU" %}

{% embed url="https://geekflare.com/anonymize-linux-traffic" %}

The `proxychains` command can be used to route your following command traffic through tor, **but** you can choose also to use proxies, not really recommended.

## DNS

### resolver

{% hint style="warning" %}
**Do not use your ISP's DNS server**
{% endhint %}

ISP DNS server is probably pointed by the default gateway ( e.g. 192.168.1.1) in your machine or configured in the router.

```
nano /etc/resolv.conf
```

### alternatives

* OpenDNS
* 1.1.1.1

## Change MAC

```
macchanger
```

### set fallback automatic random MAC address

{% embed url="https://www.youtube.com/watch?index=23&list=PLYmlEoSHldN7HJapyiQ8kFLUsk_a7EjCw&v=ELQqqXTL2XI" %}

### crontab

```
@reboot macchanger -r <your interface>
```

didn't work for me... So.

### systemd

1. create your .service file
2. make your script executable
3. Place it in `/etc/systemd/system`
4. test it
5. enable at startup

#### create `start_once.service`

```
[Unit]
Description=Run Once At Startup

[Service]
ExecStart=/path/to/start-all

[Install]
WantedBy=multi-user.target
```

#### create `start-all`

```bash
#!/bin/bash 
macchanger -r eth0
```

#### make script runnable

```
 chmod u+x /path/to/start-all
 # Access: (0744/-rwxr--r--) 
 # if someone find a method to edit this file you have a problem ahahah
```

#### move `start_once.service`

```
sudo mv start_once.service /etc/systemd/system
```

#### test

```
sudo systemctl start start_once
```

#### enable at startup

```
sudo systemctl enable start_once
```
