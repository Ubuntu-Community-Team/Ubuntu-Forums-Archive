---
title: "Mysql and phpmyadmin problems"
date: 2009-05-09
forum: x86 64-bit Users
---

### Post by maryusake on 2009-05-09
Hi all, I'm pretty new in Ubuntu 0.04. I've installed LAMP, mysql and phpmyadmin. I want a simple thing: to install  wordpress in localhost.
So, I have copyed the „phpmyadmin” to /var/www and typed in my browser „localhost/phpmyadmin” 
Till here, perfect. But, I've forgot my username and password, and I don't know from where I cand create a new user.
Besides, it shows me an error wich  I think that refers to configuration.
Can you please send me a noob tutorial about mysql(install etc)
Thx!

---

### Post by esdaniel on 2009-05-09
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

hth.

---

### Post by maryusake on 2009-05-10
Thanks, I've managed to install mysql and phpmyadmin. I also installed wordpress and everything was perfect yesterday.
Without changeing something, today I couldn't start localhost,phpmyadmin and mysql. I don't know why.
It says 
```
root@maryusake-desktop:/home/maryusake# sudo /etc/init.d/mysql start
 * Starting MySQL database server mysqld                                 [fail] 
root@maryusake-desktop:/home/maryusake# mysql -u root
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)


```

Why? Can u please help me?

---

### Post by mantelo on 2009-05-11
Hi there,

i'm going through a similar process and encountered some of your difficulties.

It seems that you restarted linux, and mysql-server wasn't started automaticly. Try "sudo mysqld_safe" to start the daemon.

This is a guide to autostart it:

[http://dev.mysql.com/doc/refman/5.1/en/automatic-start.html](http://dev.mysql.com/doc/refman/5.1/en/automatic-start.html)



Good luck!

---

