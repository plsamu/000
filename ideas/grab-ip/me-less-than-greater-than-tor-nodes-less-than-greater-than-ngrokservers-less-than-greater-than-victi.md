# Me <=> Tor nodes <=> Ngrokservers <=> victim

{% embed url="https://0x00sec.org/t/ngrok-over-tor-proxy-what-should-i-do/6237" %}

## TOR

### Install TOR

```bash
sudo nano /etc/apt/sources.list
# add
deb http://deb.torproject.org/torproject.org wheezy main
sudo apt-get update
sudo apt install tor
```

### Start TOR

```bash
sudo systemctl start tor
# check status
sudo systemctl status tor
```

## Setup proxychains4

{% embed url="https://geekflare.com/anonymize-linux-traffic/" %}

```
sudo systemctl restart tor
```

## Setup proxychains4

```
sudo nano /etc/proxychains4.conf 

# update

[ProxyList]
# add proxy here ...
# meanwile
# defaults set to "tor"
# socks4        127.0.0.1 9050
socks5  127.0.0.1 9050
```

### Try it out

```
proxychains4 firefox https://check.torproject.org/
```

## Ngrok

### Install

```
wget https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-v3-stable-linux-amd64.tgz
sudo tar xvzf ./ngrok-v3-stable-linux-amd64.tgz -C /usr/local/bin
```

### Setup

* sing in
* verify email
* add token

```
ngrok config add-authtoken <token>
```

## Setup server

```javascript
let http = require('http')

http.createServer(async (req, res) => {
    console.log(req);
    res.writeHead(200);
    res.end(`kek`);
}).listen(8080);
```

```
node index.js
```

### Launch

{% hint style="danger" %}
DIDN'T WORK (Ծ‸ Ծ)
{% endhint %}

```
proxychains4 ngrok http 8080
```

## Configure ngrok

```
nano ~/.config/ngrok/ngrok.yml

# add
proxy_url: "socks5://localhost:9050"
```

```
ngrok http --config=./ngrok.yml 8080 
```

{% hint style="danger" %}
ERROR: Your account is not authorized to run the agent with socks5 proxy.&#x20;

\
ERROR: Upgrade to an Enterprise plan at: https://dashboard.ngrok.com/billing/subscription



ERROR: ERR\_NGROK\_9010
{% endhint %}

## Fuuuk \~(^-^)\~

## Ideas

* VPS
* TailsOS
* redirect all connection to TOR (system wide global proxy)

## System wide global proxy

{% embed url="https://forums.kali.org/showthread.php?17981-Use-a-system-wide-proxy=" %}

{% hint style="info" %}
Close everything that occupies port 8080
{% endhint %}

```
Settings Manager
  > Advance Network Configuration
    > Wired
      > Gear Icon
        > 
           
```
