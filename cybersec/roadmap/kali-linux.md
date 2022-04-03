# Kali Linux

{% embed url="https://www.youtube.com/watch?index=5&list=PLYmlEoSHldN7HJapyiQ8kFLUsk_a7EjCw&v=qqatjSPIbcA" %}

```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

# check at sourcelist
sudo nano /etc/apt/sources.list
```

### Default Terminal Shortcut

```
ctrl+alt+T           open terminal
shift+ctrl+T         open new window
shift+ctrl+W         close window

shift+ctrl+R         open right view
shift+ctrl+D         open bottom view
shift+ctrl+E         close focused view
```

### change user

```bash
sudo adduser username
# add new user to sudoers
sudo usermod -aG sudo username

# change current user password
passwd
# or
passwd username

# reboot
# log to new user
# delete old user
sudo deluser kali
```
