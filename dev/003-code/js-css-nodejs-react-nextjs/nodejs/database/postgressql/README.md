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

{% hint style="info" %}
Use Pool if you expect multiple access to database
{% endhint %}

## Create Table

```sql
DROP TABLE IF EXISTS events;

CREATE TABLE IF NOT EXISTS events (
    name VARCHAR(255), 
    address VARCHAR(255)
);
```

```javascript
let create_table_events = fs.readFileSync("./sql/events.sql", "utf8");
pool.query(create_table_events, (err, res) => {
  if (err) {
    console.log(err);
    return;
  }
  console.log(res);
});
```
