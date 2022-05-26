# NodeJS + Express + PostgreSQL

{% embed url="https://glaucia86.medium.com/developing-a-crud-node-js-application-with-postgresql-d25febb1cc4" %}

## Concept

{% hint style="info" %}
Good practice is:\
\- Credentials via body\
\- Token via header\
Note that both are encrypted when using HTTPS
{% endhint %}

## Setup

```
npm init -y
npm install --save pg express dotenv
npm install -g nodemon
```

## Filetree

```
package.json
src
    sql
        events.sql
    index.js
    db.js
    config.js
.env
```

## config.js && .env

```javascript
// config.js
module.exports = {
  serverPort: "3000",
};
```

```
// .env
PORT=3000
```

## package.json

```json
{
  "name": "nodejs_postgresql_conn",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "develop": "nodemon ./src/index.js"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
    "express": "^4.18.1",
    "pg": "^8.7.3"
  }
}
```

## PostgreSQL

```sql
// events.sql

// DROP TABLE IF EXISTS events;
CREATE TABLE IF NOT EXISTS events (
    title VARCHAR(255) NOT NULL, 
    place VARCHAR(255) NOT NULL,
    date DATE NOT NULL,
    other VARCHAR(1000)
);
```

```javascript
const { Pool, Client } = require("pg");
const fs = require("fs");
// let conString = "postgres://YourUserName:YourPassword@localhost:5432/YourDatabase";
const pool = new Pool({
  user: "pi",
  host: "localhost",
  database: "db1",
  password: "pwd",
  port: 5432,
});

let create_table_events = fs.readFileSync("./src/sql/events.sql", "utf8");
pool.query(create_table_events, (err, res) => {
  if (err) {
    console.log(err);
    return;
  }
  console.log(res);
});
```

## index.js

```javascript
const db = require('./db')
var config = require('./config')
require('dotenv').config()
const express = require('express')
const app = express()
const port = process.env.PORT || config.serverPort;

app.get('/', (req, res) => {
  res.send('Hello World!')
})

app.post('/', (req, res) => {
  console.log(JSON.stringify(req.headers));
  let token = req.headers['x-access-token'] || req.headers['authorization'];
  if (token) {
    jwt.verify(token, config.secret, (err, decoded) => {
      if (err) {
        return res.json({
          success: false,
          message: 'Token is not valid'
        });
      }
      req.decoded = decoded;
      next();
    });
  } else {
    return res.json({
      success: false,
      message: 'Token not provided'
    });
  }
})

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`)
})
```
