---
title: "mysql-devel on ubuntu server with LAMP"
date: 2007-09-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by tonyalbers on 2007-09-21
Hello,

Having installed the system, I need to have mysql-devel on it too, but this happens:

root@hugin:/# uname -a
Linux hugin 2.6.20-15-server #2 SMP Sun Apr 15 06:22:36 UTC 2007 x86_64 GNU/Linux

root@hugin:/# apt-get install mysql-devel
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package mysql-devel
root@hugin:/#   

What's wrong? I've been able to install other stuff using apt-get, so I can't really figure it out.

Thanks,

Tony

---

### Post by LiLoather on 2007-09-23
I need it too but as far as I can tell from Google it isn't available for, and isn't compatible with, Ubuntu despite the fact that a great many MySQL functions depend on it.

I expect the Ubuntu developers had their reasons but, like God's reasons for making flies, forgot to tell us why.

---

### Post by schwagner on 2008-01-08
I ran into the same problem too, and I found the package is there, it's just called something funky.  Try the package libmysql++-dev and see if that works for you.

---

### Post by screavics21 on 2008-01-22
Hello everyone,

Kinda of a late delay but I was curious about this issue to. Here is a fix for the devel issue that you have with you type:

> apt-get install mysql-devel

REPLACE THAT WITH:

> apt-get install libmysqlclient12-dev libmysqlclient12


---

### Post by pietro2580 on 2008-04-03
The solution of schwagner works fine with libmysql++-dev
apt-get install libmysql++-dev

thanx!

---

