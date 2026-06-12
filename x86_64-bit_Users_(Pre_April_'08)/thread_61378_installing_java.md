---
title: "installing java"
date: 2005-08-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tux_army on 2005-08-31
Helllo i'm trying to install jre-1_5_0_04-linux-amd64-rpm.bin but i keep  getting an error message stating
> 
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)
error: cannot open Packages database in /var/lib/rpm

I'm not really familiar with the debian system or rpm thing. I came from SUSE before moving to Ubuntu and SUSE pretty much had laid out everything for me.

Any ideas?

---

### Post by DJ_Max on 2005-08-31
Try not to use RPM's.
[https://wiki.ubuntu.com/JavaAMD64](https://wiki.ubuntu.com/JavaAMD64)

---

### Post by Kuolio on 2005-08-31
To add javasupport the easy way, put tamirs repository from the "amd64 packages" thread to your sources.list. Then do "sudo apt-get install sun-j2re1.5" or check tamirs package list for the java version you like most. And thats it, then you'll have Java.

Leaving Tamirs repository enabled will give you acces to all those packages listed on that thread, so (in my opinnion) it's good to be left enabled.

If you dont know how to update your repositories, please go to ubuntu wiki --> user documentation and search for instructions.

---

### Post by mlomker on 2005-08-31
[QUOTE=Kuolio]Leaving Tamirs repository enabled will give you acces to all those packages listed on that thread, so (in my opinnion) it's good to be left enabled.
[/QUOTE]

Just to clarify--that allows you to run java applications but not java within a browser.  Sun doesn't currently have a java plug-in for AMD64.  I downloaded [Blackdown's](http://www.blackdown.org/java-linux/java2-status/index.html)  1.4.2 release and it'll work within a browser...have had it crash a few times, but it's better than nothing.

---

### Post by Tux_army on 2005-09-01
Thanks for help guys - i've got java working now.

---

### Post by Tamir on 2005-09-01
[QUOTE=mlomker]Just to clarify--that allows you to run java applications but not java within a browser.  Sun doesn't currently have a java plug-in for AMD64.  I downloaded [Blackdown's](http://www.blackdown.org/java-linux/java2-status/index.html)  1.4.2 release and it'll work within a browser...have had it crash a few times, but it's better than nothing.[/QUOTE]
 I have blackdown in my repository as well :)

---

