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

# honorable mentions
# npm install --save jsonwebtoken
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

// DATE != TIMESTAMP
// DROP TABLE IF EXISTS events;
CREATE TABLE IF NOT EXISTS events (
    title VARCHAR(255) NOT NULL, 
    place VARCHAR(255) NOT NULL,
    date TIMESTAMP NOT NULL,
    other VARCHAR(1000)
);
```

```javascript
const { Pool, Client } = require("pg");
const fs = require("fs");
const path = require("path");
const utils = require("./utils");
// let conString = "postgres://YourUserName:YourPassword@localhost:5432/YourDatabase";
const pool = new Pool({
  user: "pi",
  host: "localhost",
  database: "db1",
  password: "pwd",
  port: 5432,
});

const eventsPath = path.resolve(__dirname, "./sql/events.sql");
let create_table_events = fs.readFileSync(eventsPath, "utf8");
pool.query(create_table_events, (err, res) => {
  if (err) {
    console.log(err);
    return;
  }
  console.log(res);
});

module.exports = {
  /**
   * 
   * @param {*} response 
   * @param {*} title 
   * @param {*} place 
   * @param {yyyy-MM-ddThh:mm:ss.000Z"} date 
   * @param {*} other 
   */
  addEvent: (response, title, place, date, other) => {
    if (
      utils.isString(title) &&
      utils.isString(place) &&
      utils.isDate(date) &&
      utils.isString(other)
    )
      pool.query(
        "INSERT INTO events (title, place, date, other) VALUES ($1, $2, $3, $4)",
        [title, place, date, other],
        (error, results) => {
          if (error) throw error;
          response.status(201).end(`${results.rowCount}`);
        }
      );
    else {
      utils.isString(title) ? "" : console.log(title);
      utils.isString(place) ? "" : console.log(place);
      utils.isDate(date) ? "" : console.log(date);
      utils.isString(other) ? "" : console.log(other);
      response.status(201).send("invalid");
    }
  },
  getAllEvents: (response) => {
    pool.query("SELECT * FROM events ORDER BY title ASC", (error, results) => {
      if (error) throw error;
      response.json(results.rows);
    });
  },
};
```

## index.js

```javascript
const db = require("./db");
const utils = require("./utils");
require("dotenv").config();
const express = require("express");
const app = express();
const port = process.env.PORT || config.serverPort;

app.get("/", (req, res) => {
  db.getAllEvents(res);
});

app.post("/", (req, res) => {
  if (utils.isTokenValid(req)) {
    let date = new Date().toISOString()
    db.addEvent(res, "title1", "", date, "");
  } else {
    return res.json({
      success: false,
      message: "",
    });
  }
});

app.listen(port, () => {
  console.log(`Example app listening on port ${port}`);
});
```
