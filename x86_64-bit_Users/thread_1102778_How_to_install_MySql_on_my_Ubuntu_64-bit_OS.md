---
title: "How to install MySql on my Ubuntu 64-bit OS"
date: 2009-03-22
forum: x86 64-bit Users
---

### Post by ariyer on 2009-03-22
I am a newbie to Linux. I am trying to install MySql on my laptop, and following are the steps that i followed to get to the stage I am at now.

1. sudo apt-get update
2. sudo apt-get dist-upgrade
3. sudo apt-get install mysql-server mysql-client
When I try to "sudo mysqladmin -u root -h localhost password 'mypassword'
", the following error comes up

$ sudo mysqladmin -u root -h localhost password 'cbeam'
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

Not sure what is wrong here, it might be simple to you, but it would be great if one can explain in lay man terms on what is wrong in this case.

-ariyer

---

### Post by Slim Odds on 2009-03-22
Sound like mysql is not running.... like it says.

Maybe
```
sudo /etc/init.d/mysql
```

Just guessing.....

---

### Post by cariboo on 2009-03-22
You also need to install the mysql-server-5.0, that is available in the repositories. Set a password for root when it asks you during the setup, or you will run into problems. 

To access the mysql console, in a terminal type:

```
mysql -u root -p
```

If mysql is installed properly you will you should be presented with something like this:

```
mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 364
Server version: 5.0.67-0ubuntu6 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql> 

```

Jim

---

### Post by ariyer on 2009-03-22
Thanks guys for your prompt response. Very much appreciated. 

I uninstalled MySQL completely and tried installing again. Now following is the error when i try to set the password

deepaarvind@deepaarvind-laptop:~$ sudo mysqladmin -u root -h 127.0.0.1 password 'cbeam'
mysqladmin: connect to server at '127.0.0.1' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

Following is the output when I try to get the status

deepaarvind@deepaarvind-laptop:~$ sudo /etc/init.d/mysql status
 * /usr/bin/mysqladmin  Ver 8.41 Distrib 5.0.67, for debian-linux-gnu on x86_64
Copyright (C) 2000-2006 MySQL AB
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL license

Server version		5.0.67-0ubuntu6
Protocol version	10
Connection		Localhost via UNIX socket
UNIX socket		/var/run/mysqld/mysqld.sock
Uptime:			20 min 32 sec

Threads: 1  Questions: 8  Slow queries: 0  Opens: 12  Flush tables: 1  Open tables: 6  Queries per second avg: 0.006


Anything I am missing ?

---

### Post by kpatz on 2009-03-22
Did you set a root password when you installed mysql?

> sudo mysqladmin -u root -h 127.0.0.1 password 'cbeam'

If you set the password already and are trying to change it, use this:

> sudo mysqladmin -u root -h 127.0.0.1 --password=old_password password 'new_password'

If you forgot the mysql root password, use these commands to reset:

```

sudo /etc/init.d/mysql stop
sudo -u mysql mysqld --skip-grant-tables
mysql
(then, from within the mysql client, type)
UPDATE mysql.user SET Password=PASSWORD('put_new_password_here') WHERE User='root';
flush privileges;
(^D to exit the mysql client)
sudo /etc/init.d/mysql restart

```

---

### Post by cariboo on 2009-03-22
An even easier way to set the root password:

```
dpkg--reconfigure mysql-server-5.0
```

set the root password when prompted.

Jim

---

### Post by kpatz on 2009-03-23
> **cariboo907 said:**
> An even easier way to set the root password:

```
dpkg--reconfigure mysql-server-5.0
```

set the root password when prompted.

Jim

Actually:
```
sudo dpkg-reconfigure mysql-server-5.0
```

Fixed it for ya. ;)

---

