---
title: "chroot &amp; mysql"
date: 2006-03-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by fatman on 2006-03-01
I am running an AMD64 box.
I have mythtv installed in a 32-bit chroot.
I have apache running in my regular 64 bit environment (hosting a page that accesses a database).

Both need mysql.  I would prefer to get the chrooted mythtv to use the existing 64 bit mysql. (right now I get a can't connect to mysql-sock error from mythtv-setup)  How would I go about setting this up?

---

### Post by FluffyElmo on 2006-03-02
Any reason why you're running MythTV in a chroot? I've had it running reliably (and fast) on 64bit for a year or more now. Install may have been a little more difficult (I eventually built from source, though I think there are .deb files now) but it went pretty smoothly.

As for your current setup, I believe you can have multiple back-ends connect to a single MySQL server. In this case I'd install the 64bit version and configure 32bit myth as if it were a backend running on a separate machine. 

You'll have to check the docs as I haven't done this myself, but I believe you just have to create the db, grant all privleges for user mythtv from 127.0.0.1 and possibly configure Myth to connect to MySQL via IP address.

But I haven't done this myself so I'm not sure, but I remember seeing documentation at mythtv.org when I was setting up.

---

### Post by FluffyElmo on 2006-03-02
Just had another thought...be sure to edit */etc/mysql/mysql.cnf* and comment out the *skip-networking* variable to allow remote TCP connections. Then restart MySQL. You may already have done this as part of your Apache set-up.

I also checked the mysql docs, and I think the first grant command below will solve any other connection problems.

>  Modifying access to the MySQL database for multiple systems

If you're going to have multiple systems accessing a master database, you must grant access to the database from remote systems. By default, the mc.sql script is only granting access to the local host.

To allow other hosts access to your master database, you can either set it up for no security at all, or with more granularity. Note that the "%" is the wildcard character in MySQL.

NOTE: The "no security" option is very dangerous unless you're in a controlled environment. This example has no security at all, and allows access from any host.

    $ mysql -u root mythconverg
    mysql> grant all on mythconverg.* to mythtv@"%" identified by "mythtv";
    mysql> flush privileges;

For a more secure setup, you can restrict which machines or subnets have access. If you have a complete DNS system operational, you could do the following:

    $ mysql -u root mythconverg
    mysql> grant all on mythconverg.* to [email]mythtv@"%.mydomain.com[/email]" identified by "mythtv";
    mysql> flush privileges;

Finally, if you just want to restrict by IP subnet (in this example, the 192.168.1. network):

    $ mysql -u root mythconverg
    mysql> grant all on mythconverg.* to mythtv@"192.168.1.%" identified by "mythtv";
    mysql> flush privileges;



---

### Post by fatman on 2006-03-02
Well, Ive had a bastard of a time getting mythtv running.  I built my HTPC over a year ago (from part received as Xmas presents in 2004)  and haven't been able to get it work reliably.  In fact one of the major reasons I switched to Ubuntu (been a Debian fan for awhile) was the lure of the AMD64 myth packages - which are broken.  When I set up my chroot for flash (which isn't quite working either, but thats a story for another day) it seemed like a simple solution.  I have complied myth from source before when the box was running Debian and I almost got there, but I couldn't get the mythfrontend patch to work.  I would like to get stuff working in 64-bit, otherwise what was the point of buying the AMD64 processor?  Sorry for blathering on, but this has been frustrating me for quite some time.  To summarize:

1.  Is there enough of a performance difference between 64 and 32 bit to be noticable?

2. I would like to run mythgame w/ xmame - my 64 bit attempt to apt-get xmame results in a program that complains about using the wrong endian format - smells like a 32 vs. 64 bit problem.  Can I run 32 xmame through 64 bit mythgame (or has anyone experience getting xmame64 working)?

3.  Is there a reliable source for the patch to compile 64 bit mythtv from source (has it been solved w/ mythtv v. 19)?

4.  What external packages were required to compile mythtv from source - the documentation appears to have some default prep-package that I can't find for AMD64?

Thanks for your response,
Fatman

---

### Post by fatman on 2006-03-02
Oh yeah - the actual problem I have with the chroot & mysql:

I have both 32 and 64 bit mysql on the box, both cannot run simultaneously.  Mythtv32 works fine with mysql32, and apache64 works fine with mysql64.  When I run mysql64, mythtv32 complains it can't connect using  /var/run/mysqld/mysqld.sock (since its inside the chroot, its really /chroot/var/run/mysqld/mysqld.sock) - which is in the chroot and I assume connects to mysql32.  But mythtv32 is chrooted and can't access the /var/run/mysqld/mysqld.sock for the 64-bit enviroment.

---

