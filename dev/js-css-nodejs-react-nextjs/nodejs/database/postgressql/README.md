# PostgreSQL Conn

```
npm i --save-dev pg
```

### general template

```javascript
const { Pool } = require("pg");
const pool = new Pool({
  user: "{user}",
  host: "{host}",
  database: "{database}",
  password: "{user_password}",
  port: { port },
});
pool.query("SELECT NOW()", (err, res) => {
  console.log(err, res);
  pool.end();
});
```

### raw connection string

```
$ psql postgresql://[user[:password]@][host][:port][,...][/dbname][?param1=value1&...]
```

```javascript
const pg = require("pg"); // const { Client } = require("pg");
let conString = "postgres://YourUserName:YourPassword@localhost:5432/YourDatabase";
let client = new pg.Client(conString);
client.connect();
```

### implementation

```javascript
const { Pool, Client } = require("pg");
const pool = new Pool({
  user: "pi",
  host: "localhost",
  database: "db1",
  password: "pwd",
  port: 5432,
});
pool.query("SELECT NOW()", (err, res) => {
  console.log(err, res);
  pool.end();
});
```

## Pool vs Client

```javascript
const { Pool, Client } = require("pg");
```

















## Remember

* remember to change the password of the database
* you can have multiple servers in the same cluster
* do everytime
  * `pg_ctl.exe -D C:\Users\S\dbs\cluster1 start`
  * psql.exe -p 5432 -U S

## Sources

* [https://blog.logrocket.com/nodejs-expressjs-postgresql-crud-rest-api-example/](https://blog.logrocket.com/nodejs-expressjs-postgresql-crud-rest-api-example/)
