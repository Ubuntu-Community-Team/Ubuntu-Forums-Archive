---
title: "Easyubuntu wont start"
date: 2006-12-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by vikrant_me on 2006-12-26
I just installed easyubuntu but it wont start nor from gui or the terminal, this is the error it gives me :

vicky@vicky-desktop:~/Desktop$ easybuntu
bash: easybuntu: command not found
vicky@vicky-desktop:~/Desktop$ easyubuntu
Unable to determine desktop environment, falling back to gksudo
/usr/lib/easyubuntu
When you get a 'Password: ' prompt, type in your user password.
System sanity check: Failed!
Errors: 
--------
Failed to connect to database: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database
dpkg: error processing mythtv-database (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database (= 0.20-0.2ubuntu2); however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mythtv-database
 mythtv
E: Sub-process /usr/bin/dpkg returned an error code (1)

EasyUbuntu is now trying to run 'dpkg --configure -a'
System sanity check: Failed!
Errors: 
--------
Failed to connect to database: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database
dpkg: error processing mythtv-database (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database (= 0.20-0.2ubuntu2); however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mythtv-database
 mythtv

EasyUbuntu will not run before these errors are fixed. Please fix them and try again
vicky@vicky-desktop:~/Desktop$

---

### Post by Azakus on 2006-12-26
Run it as sudo.
```
sudo easyubuntu
```

---

### Post by vikrant_me on 2006-12-26
nop didnt work!

---

