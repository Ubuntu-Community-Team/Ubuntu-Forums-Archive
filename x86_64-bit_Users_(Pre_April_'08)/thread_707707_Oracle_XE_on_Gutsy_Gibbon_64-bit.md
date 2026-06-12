---
title: "Oracle XE on Gutsy Gibbon 64-bit?"
date: 2008-02-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by GeekLove_JavaStyle on 2008-02-25
Hello All,
Does anyone know how to install Oracle XE on amd64 Gutsy Gibbon? 

I tried the following:

steven@xxx:~/Desktop$ sudo dpkg -i oracle-xe_10.2.0.1-1.0_i386.deb 
[sudo] password for steven:
dpkg: error processing oracle-xe_10.2.0.1-1.0_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 oracle-xe_10.2.0.1-1.0_i386.deb

Any help would be greatly appreciated.

Thanks in Advance,
Steven

---

### Post by jespdj on 2008-03-11
You get the error because the package is for 32-bit Linux instead of 64-bit Linux.

It's possible to install the package with dpkg anyway (I think with --force-architecture if I remember correctly) but that will not install any dependencies, if there are any. It may not work correctly if you force-install it this way.

(I found your post because I have the same question... didn't try to force-install it yet).

---

### Post by momsab on 2008-03-11
First, read [http://www.oracle.com/technology/software/products/database/xe/files/install.102/b25144/toc.htm#BABHICJH](http://www.oracle.com/technology/software/products/database/xe/files/install.102/b25144/toc.htm#BABHICJH)
Then 
sudo dpkg -i --force-architecture oracle-xe_10.2.0.1-1.0_i386.deb

etc etc

---

### Post by jespdj on 2008-03-12
I've now installed it on my 64-bit Ubuntu system. It was not very difficult. I had only one missing library: libaio, so I manually downloaded (not via the package manager) the [i386 version of libaio1](http://packages.ubuntu.com/gutsy/i386/libaio1) and installed it:
```
sudo dpkg -i --force-architecture libaio1_0.3.106-5ubuntu2_i386.deb
```
I downloaded the Universal (Unicode) version of Oracle XE (big download, 262 MB) and installed it:
```
sudo dpkg -i --force-architecture oracle-xe-universal_10.2.0.1-1.0_i386.deb
```
And followed the instructions in the installation manual, and it works!

---

