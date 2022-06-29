# remote server on LAN

## Setup server

```bash
ssh pi@192.168.x.x
cd /home/pi/repos
mkdir mproj && cd ./mproj
git init --bare
git daemon --verbose --base-path=/home/pi/repos --export-all --reuseaddr --enable=receive-pack
```

## Client side

```bash
git clone git://192.168.x.x/mproj
```

```bash
cd ./mproj
touch README.md
git add .
git commit -m "tadaaaa"
git push origin master
```

## Get file from bare repo

{% embed url="https://stackoverflow.com/questions/12450245/getting-a-working-copy-of-a-bare-repository" %}

## Errors

{% embed url="https://superuser.com/questions/1478522/git-push-to-remote-repository-hangs-at-writing-objects-100" %}

{% embed url="https://stackoverflow.com/questions/7104182/git-push-halts-on-writing-objects-100" %}

## Simple GIT LAN Server Service

```
```
