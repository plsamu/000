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

```bash
if [ "$color_prompt" = yes ]; then
    PS1='┌─ ${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\n└──╼ '
else
    PS1='┌─ ${debian_chroot:+($debian_chroot)}\u@\h:\w\n└──╼ '
```

#### example

```bash
┌─ user@os:~
└──╼ ls
```
