# Linux

### add user to sudoers

```
su
/usr/sbin/usermod -aG sudo username

-a, --append
           Add the user to the supplementary group(s). Use only with the
           -G option.
```

```bash
su
nano /etc/sudoers
# username ALL=(ALL:ALL) ALL
```

### PS1

{% embed url="https://ezprompt.net" %}
