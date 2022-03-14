# rsync

{% embed url="https://www.youtube.com/watch?v=qE77MbDnljA" %}

### copy recursive

```bash
# copy the entire folder, not only the content
rsync -a /path/to/folder2save /path/to/backup_folder
```

### copy recursive with compression

```
rsync -za /path/to/folder2save /path/to/backup_folder
```

### copy from remote to local with ssh (port 22)

```
rsync -za user@host:/path /path/to/local
```

#### different port

```
rsync -za -e 'ssh -p 2222' --progress user@host:/path /path/to/local
```

## rsync on Windows 10

### enable dev mode

{% embed url="https://answers.microsoft.com/en-us/insider/forum/all/how-to-enable-the-windows-subsystem-for-linux/16e8f2e8-4a6a-4325-a89a-fd28c7841775" %}

### Install WSL

```
Microsoft Store > Debian > download
```

Or

```
wsl --install -d Debian
```

{% hint style="info" %}
Idk, ended up installing git bash...\
[https://prasaz.medium.com/add-rsync-to-windows-git-bash-f42736bae1b3](https://prasaz.medium.com/add-rsync-to-windows-git-bash-f42736bae1b3)
{% endhint %}
