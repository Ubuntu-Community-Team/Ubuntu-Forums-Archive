---
title: "[SOLVED] Mysql Administrator"
date: 2008-12-16
forum: x86 64-bit Users
---

### Post by kcreek33 on 2008-12-16
I am trying to setup the mysql administrator program so I can manage a remote mysql database of my web host.  I'm using a 64-bit edition of ubuntu via the Wubi installer.

On the remote host, I have added the ip address of my location (static) and everything else I know of, but cannot connect.  It works from a mysql program I use from Windows.  Here is the error message I receive:

Could not connect to host '***remote hostname***'.
MySQL Error Nr. 2003
Can't connect to MySQL server on '***remote hostname***' (111)

Any help is greatly appreciated.

---

### Post by joebeasley on 2008-12-17
I'm running 64 bit on an AMD.  I got this error when I tried to connect without sending the correct password. (left the password box blank.)  Sending the wrong password returned error 1045. 

Try connecting from the command line to see if you have access.  

mysql -u user -h host -p

---

### Post by kcreek33 on 2008-12-17
I tried it and got this error message:

ERROR 2003 (HY000): Can't connect to MySQL server on 'booksforfunds.com' (111)

---

### Post by kcreek33 on 2008-12-18
The error occurred because of various settings of my web host, which have been resolved now.  The solution included using an ssh tunnel to connect to mysql.

---

