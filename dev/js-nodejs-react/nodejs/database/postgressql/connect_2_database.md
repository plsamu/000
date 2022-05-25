# connect to database

## Get the port

```
\conninfo
```

## Show tables

```bash
\c music_live_city_list     # select database
\dt                         # show tables
# e ovviamente...
SELECT * FROM <nome_tabella>;  # per leggere la tabella
```

## Drop table

```bash
DROP TABLE [ IF EXISTS ] name [, ...] [ CASCADE | RESTRICT ];
# or
DROP TABLE IF EXISTS artist CASCADE;  # punto e virgola, SEMPRE!
```
