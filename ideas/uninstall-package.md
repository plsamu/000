# Uninstall package

{% embed url="https://superuser.com/questions/513159/how-to-remove-systemd-services" %}

```bash
sudo ./uninstall_package <pkg_name>
```

```bash
#!/bin/bash

if [[ $EUID -ne 0 ]]; then
   echo "This script must be run as root, use sudo "$0" instead" 1>&2
   exit 1
fi

# ====================================================
# check args
# $# -> tell the number of input arguments
# ====================================================

if [ $# -eq 0 ]; then
    echo "ERROR: no arguments supplied"
    echo ""
    echo "Example:"
    echo "  uninstall_package <pkg-name>"
    exit 1
elif (( $# > 1 )); then
    echo "ERROR: too many arguments"
    echo ""
    echo "Example:"
    echo "  uninstall_package <pkg-name>"
    exit 1
fi

# ====================================================
# check services
# ====================================================

tmp=$(systemctl list-units --full -all | grep -F "$1.service")
size=${#tmp}

if (( $size == 0 )); then
    echo "> None service found"
else
    echo "> Service found"
    systemctl stop $1
    systemctl disable $1

    rm /etc/init.d/$1
    rm /etc/systemd/system/$1
    rm /etc/systemd/system/$1 # and symlinks that might be related
    rm /usr/lib/systemd/system/$1
    rm /usr/lib/systemd/system/$1 # and symlinks that might be related

    systemctl daemon-reload
    systemctl reset-failed
fi

# ====================================================
# uninstall package
# ====================================================

apt-get remove $1
```
