---
title: "K3b problems"
date: 2006-05-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by Davidosky on 2006-05-09
Hi all,
I'm a Kubuntu 64bit Dapper Drake user. :) 
When i try to launch "k3b" from MenuK or from Konsole i haven't any error but K3b doesn't start. ](*,) 

What can i do? :confused:

---

### Post by cyracks on 2006-05-09
I don't know if this will give you any relevant errors but try

$gdb k3b
run

---

### Post by Davidosky on 2006-05-09
When i start gdb k3b:
> gdb k3b
GNU gdb 6.4-debian
Copyright 2005 Free Software Foundation, Inc.
GDB is free software, covered by the GNU General Public License, and you are
welcome to change it and/or distribute copies of it under certain conditions.
Type "show copying" to see the conditions.
There is absolutely no warranty for GDB.  Type "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu"...(no debugging symbols found)
Using host libthread_db library "/lib/libthread_db.so.1".

(gdb)


> (gdb) run
Starting program: /usr/bin/k3b
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 46912580652208 (LWP 5576)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
---Type <return> to continue, or q <return> to quit---
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
                                  

---

