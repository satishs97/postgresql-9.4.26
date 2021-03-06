# How to setup postgres from source code

## Installetion :
- After downloding the [postgres source code](https://www.postgresql.org/ftp/source/v9.4.26/)  run the following cmds:
- `    ./configure `
- `    make `
- `    su ` (To change root password: sudo passwd root)
- `    make install  `
- `    adduser postgres    ` (create user for postgres)
- `    mkdir <data_directy_path>   ` (eg. mkdir ~/mycluster)
- `    chown postgres <data_directy_path> ` (eg. chown postgres ~/mycluster)
- `    su postgres `

## Configuration :
-   Open 'vim ~/.bashrc' file and add below lines.
``` 
    export LD_LIBRARY_PATH=/usr/local/pgsql/lib  
    export PATH=/usr/local/pgsql/bin:$PATH 
```
- ` export PGDATA=$HOME/mycluster `
- ` source ~/.bashrc ` (Reload shell)

**NOTE:** This ".bashrc" file is diffrent from you local machine make sure you are login with postgres user.

### Now you can directly use psql cmds :
- ` initdb -D <data_directy_path> ` (The "-D" option specifies the location where the data will be stored.)
- ` postgres -D <data_directy_path> >logfile 2>&1 & `
- eg. ` initdb -D ~/mycluster `
- eg. ` postgres -D ~/mycluster >logfile 2>&1 & `
- ` pg_ctl start `     (start psql server)

### To check server is running run below cmd: 
- ` pg_ctl status `         
        pg_ctl: server is running (PID: 10246)
        /usr/local/pgsql/bin/postgres

- ` psql --version`
- ` psql ` (optional: psql -U shubham -d shubham)

## To work on psql everytime run only following cmds:
- ` su postgres`
- ` pg_ctl start ` (press CLT+c after this cmd)
- ` psql `
- ` pg_ctl restart ` (To restart server )