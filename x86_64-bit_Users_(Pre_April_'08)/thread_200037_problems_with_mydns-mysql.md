---
title: "problems with mydns-mysql"
date: 2006-06-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by smellyfis on 2006-06-19
i am trying to get a webserver up and running and when i tried to install mydns-mysql the installation always brealks and spits out this line of code

```
:~$ sudo dpkg --configure -a
Setting up mydns-mysql (1.1.0+pre-3) ...
/etc/mydns.conf created/modified. See mydns.conf(5) for details.
A backup of the old config file is at /etc/mydns.conf.dpkg-old. Values
were preserved, except for database information (database,db-*).
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using passwor                                                                  ES)
Creating database...
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: YES)'
dpkg: error processing mydns-mysql (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mydns-mysql
``` how do i either finish or remove this installation other wise adept is stuck and i cannot install anything else

---

### Post by linuchsan on 2006-06-19
There is only access for root@localhost in mysql.
Try:
GRANT ALL PRIVILEGES ON *.* TO root@127.0.0.1 IDENTIFIED BY '' WITH GRANT OPTION;

---

### Post by smellyfis on 2006-06-19
I tried that inside of mysql and it did not help i also changed 127.0.01 to localhost and that did not help either
thank you thou

---

### Post by linuchsan on 2006-06-20
You can try to start mysql-server with the --debug option to find the problem.

---

### Post by smellyfis on 2006-06-21
I figured out what happened. I set the password for Mydns to use for mysql  differently for what it was actually. i fixed it.

---

