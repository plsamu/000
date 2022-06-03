# create - GIT LAN Server Service

## Code

```javascript
const exec = require("child_process").exec;

let command =
  "git daemon --verbose --base-path=/home/pi/repos --export-all --reuseaddr --enable=receive-pack";

console.log(command);

exec(command, (err, stdout, stderr) => {
  if (err) throw err;
  console.error(stderr);
  console.log(stdout);
});
```

## Service

```bash
touch git_lan_server.service
```

```systemd
[Unit]
Description=git lan server service
After=network.target
StartLimitIntervalSec=0

[Service]
Type=simple
Restart=always
RestartSec=1
User=<user>                                        // CHANGE
ExecStart=</usr/bin/env node /path/to/server.js>   // CHANGE

[Install]
WantedBy=multi-user.target
```

```bash
sudo mv git_lan_server.service /etc/systemd/system/
systemctl start git_lan_server
systemctl enable git_lan_server
```
