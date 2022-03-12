# sed

By default, `sed` uses BRE and would need `-E` or `-r` option to use ERE.\
Meaning you can use "?" command. E.g:

#### get \*full raw command\* apt manually installed packages

```
zcat /var/log/apt/history.log.*.gz | sed -r '/Commandline: apt(-get)? install/!d'
```

