# Fast, minimal, with wifi

{% hint style="info" %}
read long buffer

1. use tmux
2. run command
3. ctrl + b
4. pres \[
5. use arrow to move the cursor

Also

1. ctrl + b
2. page-up
{% endhint %}

### ip link, netctl

```bash
ip link set {interface} up

# create profile
wifi-menu
ip link set {interface} down

# start profile
netctl start {profile created}
```

### iwctl

```bash
iwctl
device list
device {interface} set-property Powered off
device {interface} set-property Powered on
station {interface} get-networks
station {interface} connect {SSID}

# check connection
station {interface} show
```

{% embed url="https://github.com/picodotdev/alis" %}

