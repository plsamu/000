# sed

By default, `sed` uses BRE (Basic Regular Expression) and would need `-E` or `-r` option to use ERE (Extended Regular Expression).

ERE means for example:

* you can use "?" command
* you don't have to escape the parens

#### get \*full raw command\* apt manually installed packages

```
zcat /var/log/apt/history.log.*.gz | sed -r '/Commandline: apt(-get)? install/!d'
```

#### full bash script to get manually installed package

```bash
#!/bin/bash 

function get_install_only_commands_1 {
	zcat /var/log/apt/history.log.*.gz | sed -r '/Commandline: apt(-get)? install/!d'
}

function remove_start_of_command_2 {
	sed -r 's/(^Commandline: apt(-get)? install)//'
}

function remove_options_3 {
	sed -r 's/(( \-[\-]?)(\w*[\-]?)*)*//'
}

get_install_only_commands_1 | remove_start_of_command_2 | remove_options_3
```

Output:

```
git
 apt-transport-https ca-certificates curl
 docker-ce-cli docker-ce
 docker-ce-rootless-extras
```
