# Onion service return public IP

## Node JS - Get public IP

### ip\_helper.mjs

```javascript
import fetch from "node-fetch";

export async function getIp() {
  const ip_raw = await fetch("https://ipinfo.io/json");
  const ip_json = await ip_raw.json();
  return ip_json.ip;
}
```

### index.js

```javascript
import { createServer } from "http";
import * as ip from "./ip_helper.mjs";

/**
 * this works only with internal request
 * aka localhost:50000
 */
createServer(async (req, res) => {
  res.writeHead(200);
  let pub_ip = await ip.getIp();
  res.end(`${pub_ip}`);
}).listen(50000, "localhost");

/**
 * delete this!
 * this capture LAN request
 * aka 192.168.1.100:50000
 */
createServer((req, res) => {
  res.writeHead(200);
  res.end(`do not`);
}).listen(50000);
```

## Open an Hidden Service and enjoy

[Setup an HS](../../ict/hidden-services-aka-onion-services/setup-an-hidden-service.md)



