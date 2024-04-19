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
