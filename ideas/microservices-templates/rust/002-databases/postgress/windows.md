# windows

## Paths example

```
Installation Directory:                    C:\Program Files\PostgreSQL\14
Server Installation Directory:             C:\Program Files\PostgreSQL\14
Data Directory:                            C:\Program Files\PostgreSQL\14\data
Database Port:                             6543
Database Superuser:                        postgres
Operating System Account:                  NT AUTHORITY\NetworkService
Database Service:                          postgresql-x64-14
Command Line Tools Installation Directory: C:\Program Files\PostgreSQL\14
pgAdmin4 Installation Directory:           C:\Program Files\PostgreSQL\14\pgAdmin 4
Stack Builder Installation Directory:      C:\Program Files\PostgreSQL\14
Installation Log:                          C:\Users\S\AppData\Local\Temp\install-postgresql.log
LOGS                                       C:\Program Files\PostgreSQL\14\data\log
```

## Configurations

```
C:\Program Files\PostgreSQL\14\data\postgresql.conf
```

```
#------------------------------------------------------------------------------
# CONNECTIONS AND AUTHENTICATION
#------------------------------------------------------------------------------

# - Connection Settings -

listen_addresses = '*'	     # what IP address(es) to listen on;
                             # comma-separated list of addresses;
                             # defaults to 'localhost'; use '*' for all
                             
port = 6543		     
```

## Auto start database cluster

```
C:\Users\S\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup
```

### open\_db\_cluster.bat

```batch
@ECHO OFF
START /B "CMD" "C:\Program Files\cmder\Cmder.exe" /TASK db_start_cluster
```

### Cmder.exe -> TASK -> db\_start\_cluster

```
pg_ctl.exe -D C:\path\to\my_cluster start
```

##

