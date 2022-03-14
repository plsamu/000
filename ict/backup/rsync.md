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

```
Microsoft Store > Debian > download
```

Or

```
wsl --install -d Debian
```
