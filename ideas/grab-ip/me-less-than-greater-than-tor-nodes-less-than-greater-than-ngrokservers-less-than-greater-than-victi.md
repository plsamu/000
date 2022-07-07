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

