---
title: "Having problem with postgresql 8.3"
date: 2008-10-06
forum: x86 64-bit Users
---

### Post by goldstar1 on 2008-10-06
I'm trying to configure postgresql 8.3 and I cant even start the server.

*I installed it using apt
*I went to the postgres doc page and it gave me this to start the server >> postgres -D /usr/local/pgsql/data

and the result was  >> bash: postgres: command not found

*I'm new at this and really want to learn something here but now I'm stumped.
Please help

---

### Post by yyyc186 on 2008-10-07
I too am running AMD 64 Hardy and after reading this message, decided to poke around.

First, you have no need to start the server.  If you rebooted your machine and watched the startup script flying by you would see that Postgres got started with the boot.

Your next problem is going to be creating and/or accessing a database.  I humbly suggest you install KDE and abandoned Gnome since KDE gives lots of nice tools for things and Gnome requires the mindset of people who live in caves and eat their young if you want to do anything other than check email or surf the Web.

From the KDE3 blue icon select System, then "KUser - User Management".  This will list all of the accounts on your system for you.  Somewhere in that list you will see a user account called "postgres".  Double click on it.  In the window which pops up, clear the checkbox which has the account disabled.  Click on the "set password" button and assign a password.  Click on OK to save everything, then get out of KUser.

Next you need to be a user and you will probably want to be a super user.

roland@roland-desktop:~/xpns$ su postgres
Password: 

postgres@roland-desktop:/home/roland/xpns$ createuser roland;
Shall the new role be a superuser? (y/n) y
postgres@roland-desktop:/home/roland/xpns$ exit
exit

Last but not least, you need to be aware that Ubuntu did its own thing with the installation.  None of that install doc put out by the PostgresSQL community is going to do you any good.  Either use the following from the command line each time you log in or create a script file to run each time you log in.

 export PATH=/usr/lib/postgresql/8.3/bin:$PATH

You will find one tree for each version of postgres installed on your machine under /usr/lib/postgresql.  There is a bin and a lib dir under each.  For many things you will probably need to define LD_LIBRARY_PATH to point to that lib dir.

This should get you farther than you were.

---

### Post by yyyc186 on 2008-10-07
In case you aren't aware, if you create a database without creating tablespace on a different drive, your database will be created in the default tablespace area which I believe is the same path your installation sits on.

roland@roland-desktop:~/xpns$ su postgres
Password: 
postgres@roland-desktop:/home/roland/xpns$ mkdir /books/db_data
postgres@roland-desktop:/home/roland/xpns$ psql
Welcome to psql 8.3.3, the PostgreSQL interactive terminal.

Type:  \copyright for distribution terms
       \h for help with SQL commands
       \? for help with psql commands
       \g or terminate with semicolon to execute query
       \q to quit

postgres=# CREATE TABLESPACE bigspace LOCATION '/books/db_data';
CREATE TABLESPACE
postgres=# \q
postgres@roland-desktop:/home/roland/xpns$ createdb --tablespace bigspace tax_2005 'Tax information for 2005';
postgres@roland-desktop:/home/roland/xpns$ dir /books/db_data
16388  PG_VERSION
postgres@roland-desktop:/home/roland/xpns$ 


roland@roland-desktop:~/xpns$ psql
psql: FATAL:  database "roland" does not exist
roland@roland-desktop:~/xpns$ psql tax_2005
Welcome to psql 8.3.3, the PostgreSQL interactive terminal.

Type:  \copyright for distribution terms
       \h for help with SQL commands
       \? for help with psql commands
       \g or terminate with semicolon to execute query
       \q to quit

tax_2005=# 


I chose to create my database out under the drive I have my books on since that is a 1TB drive and when it runs out of room it won't crash my system.  Run out of room on your system drive and you will have all sorts of issues.

---

### Post by goldstar1 on 2008-10-07
Okay...I'll try installing KDE and go from there...I also was having trouble installing pgplus advance server bundle from their website without God blessing me with success.

Thanks for your quick response.

---

