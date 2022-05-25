# PostgreSQL

{% embed url="https://opensource.com/article/17/10/set-postgres-database-your-raspberry-pi" %}

## Setup and init

{% hint style="info" %}
The database system will be owned by user "postgres"
{% endhint %}

### Start the server

```bash
sudo systemctl start postgresql@13-main
# sudo systemctl enable postgresql@13-main     start the server on boot
sudo systemctl status postgresql@13-main       # check status
```

### Create user (do not use default)

```
sudo -u postgres createuser $(whoami) --createdb
```

#### Modify a user

```bash
sudo -u postgres psql
\du
ALTER USER <user_name> WITH CREATEDB;
\q
# no need to "exit"
```

### Create DB

```
createdb <db_name>
```

### Open database

```bash
psql -U Username DatabaseName
# or
psql <db_name>
```

