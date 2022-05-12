# Protect the response

* encrypt with public gpg
* use a token

## Use a token

```
get_public_ip
    .env
    form.html
    index.js
    ip_helper.mjs
    package.json
```

### package.json

```json
"dependencies": {
    "dotenv": "^16.0.1",
    "node-fetch": "^3.2.4",
    "nodemon": "^2.0.16"
}
```

```
npm install --save node-fetch dotenv nodemon
```

### index.js

```javascript
import * as dotenv from "dotenv";
dotenv.config();
import * as fs from "fs";
import { createServer } from "http";
import * as ip from "./ip_helper.mjs";

let formHtml = fs.readFileSync("./form.html");
let port = 50000;

createServer(async (req, res) => {
  switch (req.url) {
    case "/": {
      res.writeHead(200);
      res.write(formHtml);
      res.end();
      break;
    }
    case "/lolip": {
      let auth = req.headers["auth"];
      if (auth === process.env.pwd) {
        res.writeHead(200);
        let pub_ip = await ip.getIp();
        res.end(pub_ip);
        break;
      } else {
        res.writeHead(400);
        res.end("nope");
        break;
      }
    }
    default: {
      res.writeHead(400);
      res.end("uccelli senza zucchero");
      break;
    }
  }
}).listen(port, "localhost");

```

### form.html

```html
<body>
  <label class="label" for="input">PWD</label>
  <input
    class="input"
    type="password"
    id="input"
    style="width: 1000px"
    onkeydown="sendReq(event)"
  />
</body>

<script>
  async function sendReq(event) {
    if (event.keyCode === 13) {
      let input = document.getElementById("input");
      let xhr = new XMLHttpRequest();
      xhr.open("GET", "/lolip", true); // true for async
      xhr.setRequestHeader("auth", input.value);
      xhr.onload = function (e) {
        if (xhr.readyState === 4) {
          if (xhr.status === 200 || xhr.status === 400) {
            document.open();
            document.write(xhr.responseText);
            document.close();
          } else {
            console.error(xhr.statusText);
          }
        }
      };
      xhr.onerror = function (e) {
        console.error(xhr.statusText);
      };
      xhr.send(null);
    }
  }
</script>
```

### .env

```
pwd=token_used_as_pwd
```
