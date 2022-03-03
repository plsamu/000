♠ faststart
===

download postgressql
---

window -> exe

create role
---

```bash
psql postgres  # connect to default db
postgres= \conninfo  # check info connection  
```

create a project
---

```bash
npm init -y

npm i express pg -save  # pg is a postgressql client to interact with postgressql server
npm i -D typescript  # -D is for devDependencies
# Create a file named tsconfig.json: configurazioni sulla source sotto
npm i -D tslint  # it is a code analysis tool to alert you to potential problems in your code beyond syntax issues
# create a new file in the root folder named tslint.json: configurazioni sulla source sotto
npm i -D nodemon @types/node @types/express @types/pg

touch src/index.ts
```

edit package.json

```json
"main": "dist/index.js",
"scripts": {
    "prebuild": "tslint -c tslint.json -p tsconfig.json --fix",
    "build": "tsc",
    "prestart": "npm run build",
    "start": "node .",
    "test": "echo \"Error: no test specified\" && exit 1"
}
```

runna tutto

```bash
npm run start
```

[source](https://developer.okta.com/blog/2018/11/15/node-express-typescript)

---

Classic express basic server:

```js
const express = require('express')
var app = express()

app.use(express.static("public"))

/** app.use(middleware) */
const middleware1 = require('./src/routes/middleware1.js')
app.use('/md1', middleware1.router)

/** server */
var server = app.listen(3333, function () {
   var host = server.address().address
   var port = server.address().port
   console.log("Example app listening at http://%s:%s", host, port)
})

process.on('uncaughtException', err => {
   console.error('There was an uncaught error', err)
   process.exit(1) //mandatory (as per the Node.js docs)
})
```
