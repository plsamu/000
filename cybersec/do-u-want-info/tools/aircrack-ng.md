---
description: Aircrack-ng is a complete suite of tools to assess WiFi network security.
---

# aircrack-ng

### monitor mode

{% embed url="https://linuxhint.com/monitor_mode_kali_linux" %}

```
sudo ip link set wlan0 down
sudo iw wlan0 set monitor control
sudo ip link set wlan0 up
```
