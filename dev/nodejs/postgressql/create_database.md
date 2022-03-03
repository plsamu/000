Create Database
===

<https://www.postgresql.org/docs/9.4/runtime.html>

1) Add the PostgreSQL bin directory path to the PATH environmental variable
    > C:\Program Files\PostgreSQL\14\bin
2) add cluster (anyway postgres dovrebbe creare un cluster di default)

    ```bash
    pg_ctl.exe -D /path/to/cluster init
    # also
    pg_ctl.exe -D C:\Users\S\dbs\cluster1 init
    ```

3) crea e connettiti al database

    ```text
    createdb.exe
    psql.exe -p 5432 -U <user_name>
    ```

psql.exe
---

```bash
\l # Mostare la lista dei database
DROP DATABASE [IF EXISTS] database_name;
CREATE DATABASE music_live_city_list;
```

THE END
---

---
---
---
---
---
---
---
---
---
---
---
---
---
---
---

Comandi base
---

```bash
psql.exe --help
psql.exe -p 6543 -U postgres -d db_name
```

RAW
---

1) segui le info e modifica
    > pg_hba.conf

    con

    ```text
    host all <username> 127.0.0.1/32 trust
    ```

After making changes to the pg_hba.conf or postgresql.conf files, the cluster needs to be reloaded to pick up the changes.
From the command line:

```bash
pg_ctl reload
```
