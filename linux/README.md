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

### Another PS1

```bash
function parse_git_branch() {
        BRANCH=`git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/\1/'`
        if [ ! "${BRANCH}" == "" ]
        then
                # STAT=`parse_git_dirty`
                # echo "[${BRANCH}${STAT}]"
                echo "[${BRANCH}]"
        else
                echo ""
        fi
}


if [ "$color_prompt" = yes ]; then
   PS1='┌─ \[\e[33m\]\A\[\e[m\]$(parse_git_branch) ${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\n└──╼ '
else
   PS1='┌─ \A $(parse_git_branch) ${debian_chroot:+($debian_chroot)}\u@\h:\w\n└──╼ '
fi
```

```
┌─ 10:57 user@os:~
└──╼ 
```
