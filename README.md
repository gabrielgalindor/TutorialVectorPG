# TutorialVectorPG
This is a quick and complete tutorial on how to install PG Vector to be read by flowise on Ubuntu 22.04


# First Steps

## Installing PostgreSQL

To install PostgreSQL, first refresh your server’s local package index:

>
>  sudo apt update
>
>
> sudo apt install postgresql postgresql-contrib

Press Y when prompted to confirm installation. If you are prompted to restart any services, press ENTER to accept the defaults and continue.

The installation procedure created a user account called postgres that is associated with the default Postgres role. There are a few ways to utilize this account to access Postgres. One way is to switch over to the postgres account on your server by running the following command:

>
>  sudo -i -u postgres
>
> psql

Then, create a new user (Role) on PostgreSQL:

>
>  CREATE USER flowise WITH PASWORD 'yourpassword';
>

Then, create a new database:
>
>  createdb datavec;
>

At now, you should grant all privileges on database with the Flowise user:
>
>  GRANT ALL PRIVILEGES ON DATABASE datavec TO flowise;
>


Once the database is created, it is necessary to install the Postgresql developer packages

## Install developer packages from PostgreSQL

Run the next command on your Ubuntu machine:
>
>  sudo apt-get install postgresql-server-dev-all
>

Now you must find the path of the "pg_config_manual.h" file. To find the pg_config_manual.h file, you can use the find command as mentioned above. Once you have found the location of the file, you can browse or use it as needed in your development process.
```sh
sudo find / -name pg_config_manual.h
```

The path that returned to me is: "/usr/include/postgresql/pg_config_manual.h". So, you must run the next command with your path:
>
>  gcc -I/usr/include/postgresql -o pg_config_manual pg_config_manual.h
>

## Install Pgvector 

Compile and install the extension (supports Postgres 12+)

```sh
cd /tmp
git clone --branch v0.6.2 https://github.com/pgvector/pgvector.git
cd pgvector
make
make install # may need sudo
```

See the [installation notes](#installation-notes---linux-and-mac) if you run into issues







