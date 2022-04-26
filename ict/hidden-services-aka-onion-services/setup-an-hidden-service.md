# Setup an Hidden Service

### [Install Tor](https://community.torproject.org/onion-services/setup/install/)

check that Tor is working:

```bash
pi@raspberrypi:/etc/apt/sources.list.d $ tor
Tor 0.4.6.10 running on Linux with Libevent 2.1.12-stable, OpenSSL 1.1.1k, Zlib 1.2.11, Liblzma 5.2.5, Libzstd 1.4.8 and Glibc 2.31 as libc.
```

check if Tor is running:

```
htop -F tor
```

search for torrc file:

```
grep -r /etc/ -e torrc
# /etc/tor/torrc
```

### [configure torrc](https://community.torproject.org/onion-services/setup/#step-2-configure-your-tor-onion-service)

```bash
sudo nano /etc/tor/torrc
# add these lines
# HiddenServiceDir /var/lib/tor/m_onion_service/
# HiddenServicePort <port> 127.0.0.1:<port>
```

{% hint style="info" %}
**Good practice**: create listening server first.
{% endhint %}

{% hint style="info" %}
**Tip:** A good practice to avoid leaking an Onion Service to a local network is to run Onion Services over Unix sockets instead of a TCP socket. You will need to edit and put the following two lines in your `torrc` file:

```
HiddenServiceDir /var/lib/tor/m_onion_service/
HiddenServicePort 80 unix:/var/run/tor-my-website.sockhinrt
```
{% endhint %}

### restart tor

```
sudo systemctl restart tor
```

### where to read the hostname?

{% hint style="info" %}
The path is showed inside the torrc file:\
`HiddenServiceDir /var/lib/tor/m_onion_service/`
{% endhint %}
