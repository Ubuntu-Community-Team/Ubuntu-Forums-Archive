---
title: "mySQL Server won't start after reboot"
date: 2006-11-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by OriUbu on 2006-11-07
Hi 

I'am new to Ubuntu, but not to Linux/Solaris/Debian. Some friend of mine have been raving about Ubuntu for months so I thought I'd give it a try.

All was going well ATI driver on my x1800 3d and everything working fine
Put in all the codec pack and now can play back all my media files.

Here comes the But .......

I have a PVR-150MCE so I thought what the hell it all been good going so far lets give mythTV a try.

Of course for this I need a mySQL server.

So I follow the install guide for 

Ubuntu 6.10 Edgy x64 Desktop that I have installed all fine.

Then I reboot to double check everything is fine (Always have to check with these things)

And now NO MATTER what I do it just fails to start


Now I could hack the hell out of the distro and use the generic download form the mySQL site. 

But I belive it's best to bring these bug to light. Since this is debian based and a Desktop version I shouldn't have to do anything fancy to get this BASIC service working.

So all you long time Ubuntu user's is this a known issue or is there a work around.


MY SPEC:
DELL 5110
ATI X1800GTO
Intel Pentium D 810
1GB MEMEORY
80GBSATA
Hot-pog PVR-150MCE

P.S. I have now done at lest 4 fresh install then only installing mySQL problem is still there.

---

### Post by OriUbu on 2006-11-07
I have now tried this with the command line server version of ubuntu and still get the same result.

---

### Post by fabertawe on 2006-11-07
I'm on Edgy and the mySQL service starts and stops here with no error. I did have MythTV installed but never used it, so removed it. I upgraded from Dapper rather than a clean install, if that makes any difference.

Is anything reported on [Launchpad]("https://launchpad.net/")? Do you have any output in the terminal with
```
sudo /etc/init.d/mysql start
```

Paul

---

### Post by OriUbu on 2006-11-07
Yup it would make a diffrence if you upgraded since your system mysql script would most likly not have changed.


This is what I get......  


orignboy@ori-ubuntu:~$ sudo /etc/init.d/mysql start
* Starting MySQL database server mysqld [fail]
orignboy@ori-ubuntu:~$

orignboy@ori-ubuntu:~$ cat /var/log/mysql.log
orignboy@ori-ubuntu:~$

orignboy@ori-ubuntu:~$ /usr/bin/mysqld_safe start
Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[31773]: started
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[31778]: ended
orignboy@ori-ubuntu:~$

---

### Post by fabertawe on 2006-11-07
> **OriUbu said:**
> Yup it would make a diffrence if you upgraded since your system mysql script would most likly not have changed.

mySql was upgraded (including the .cnf, it asked me), unless you meant something else (I know little about it).

> This is what I get......  

orignboy@ori-ubuntu:~$ sudo /etc/init.d/mysql start
* Starting MySQL database server mysqld [fail]
orignboy@ori-ubuntu:~$

orignboy@ori-ubuntu:~$ cat /var/log/mysql.log
orignboy@ori-ubuntu:~$

orignboy@ori-ubuntu:~$ /usr/bin/mysqld_safe start
Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[31773]: started
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[31778]: ended
orignboy@ori-ubuntu:~$

I just reinstalled the following...
mysql-client
mysql-client-5.0
mysql-common
mysql-server
mysql-server-5.0

and it's still working here. 

I don't have a '/var/run/mysqld/mysqld.pid'. You could try renaming this. I'm out of my depth now, hopefully someone else can take over!

Paul

---

### Post by digifork on 2006-11-07
I was having the same issue and just fixed it.

My problem was I relocated the data directory from /var/lib/mysql to /data/mysql (on another partition) by editing the datadir attribute in the my.cnf.

Since this was a fresh install, I just let MySQL create a new ib data files. The problem was, I needed the debian-5.0.flag, mysql_upgrade.info, and all the other junk in the /var/lib/mysql directory in order for MySQL to work.

To fix it, I removed the /data/mysql directory and ran 'sudo mv /var/lib/mysql /data'. It runs just fine now.

Your problem is probably different. I think MySQL should work on logging startup errors better because I still don't know the specific reason it wasn't starting in the first place.

-digi

---

### Post by OriUbu on 2006-11-08
Thanks digifork. Looks like I am going to some editting, would be nice to know if this is happening to other people on a fresh install cause I dont want to go shouting about it being a huge but in Ubuntu.

But if it is I think its very poor that this wasn't tested for. mySQL is very common app these days and a core part of mythtv.

---

### Post by OriUbu on 2006-11-08
Well I'm sorted the problem but .... It just keeps happening on reboot and I don't want to dump and reinstall the data dir every time I reboot.


So I've switched to the 32-bit version and all is well :D 

I'll have to come back to the 64-bit in a few months.

---

