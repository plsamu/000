---
description: Raspberry Pi 4 (armv8) compliant
---

# MariaDB

{% hint style="info" %}
MariaDB is a community-developed, commercially supported fork of MySQL.
{% endhint %}

```
sudo apt install mariadb-server
```

Then follow tutorial like: _How to use MySQL database in Next.js apps_

## Connection

### create lib/db.js and .env.local

```
pages
    - index.js
public
lib
    - db.js
.env.local
```

#### db.js

```tsx
import mariadb from "mariadb";

const pool = mariadb.createPool({
  host: process.env.DB_HOST,
  user: process.env.DB_USER,
  password: process.env.DB_PASSWORD,
  connectionLimit: 5,
});

export default async function excuteQuery({ query, values }) {
  let conn;
  try {
    conn = await pool.getConnection();
    let results;
    if (values) results = await conn.query(query, values);
    else results = await conn.query(query);
    console.log(results);
    return results;
  } catch (error) {
    // throw error;
    return { error };
  } finally {
    if (conn) return conn.end();
  }
}
```

#### .env.local

```
DB_HOST= 127.0.0.1
DB_PORT= {port}          // mariadb default port 3306
DB_DATABASE= {db name}
DB_USER= {user}          //user here
DB_PASSWORD= {password}  //password here
```
