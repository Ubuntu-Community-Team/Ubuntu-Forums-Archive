---
title: "Can't Update/ Install anything"
date: 2008-10-13
forum: x86 64-bit Users
---

### Post by Oh_Buhnanerz on 2008-10-13
No matter what I try to install using the add/ remove applications or how I try to update I have this same error message: 

"failed in buffer_read(fd)"

I am fairly new to Ubuntu and have always figured how to fix things but this has me stumped.:confused::mad:](*,)

Thanks in advance :p

---

### Post by Jouke74 on 2008-10-14
Hi Oh_Buhnanerz, something likely got broken with the package manager, you probably have downloaded a corrupt DEB somewhere.

Open up a terminal and try the following commands first:
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoclean

If this fails then try the following solution: 
[http://exain.wordpress.com/2007/12/03/failed-in-buffer_readfd-on-ubuntu/](http://exain.wordpress.com/2007/12/03/failed-in-buffer_readfd-on-ubuntu/)

---

### Post by Oh_Buhnanerz on 2008-10-15
> **Jouke74 said:**
> Hi Oh_Buhnanerz, something likely got broken with the package manager, you probably have downloaded a corrupt DEB somewhere.

Open up a terminal and try the following commands first:
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoclean


during the upgrade I received this message:
```
(Reading database ... dpkg: error processing /var/cache/apt/archives/linux-libc-dev_2.6.24-21.42_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `sun-java6-jre': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/linux-libc-dev_2.6.24-21.42_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
and the second suggestion only is if you have a corrupt package, every package I attempt to install or uninstall, gives back that same error. "failed in buffer_read(fd)" so every package cannot be corrupt.

---

### Post by Oh_Buhnanerz on 2008-10-18
:BUMP: 

I am still in need of help :((

---

