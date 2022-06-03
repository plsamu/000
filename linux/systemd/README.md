# systemd

## Remove

{% embed url="https://superuser.com/questions/513159/how-to-remove-systemd-services" %}

```bash
systemctl stop [servicename]
systemctl disable [servicename]
rm /etc/init.d/[servicename]
rm /etc/systemd/system/[servicename]
rm /etc/systemd/system/[servicename] # and symlinks that might be related
rm /usr/lib/systemd/system/[servicename] 
rm /usr/lib/systemd/system/[servicename] # and symlinks that might be related
systemctl daemon-reload
systemctl reset-failed
```

## Utils

```bash
systemctl list-unit-files
ls /etc/systemd/system/
```

```bash
systemctl cat [servicename]
```
