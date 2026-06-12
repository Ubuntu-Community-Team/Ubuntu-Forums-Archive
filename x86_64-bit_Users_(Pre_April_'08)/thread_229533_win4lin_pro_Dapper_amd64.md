---
title: "win4lin pro Dapper amd64"
date: 2006-08-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by NetJumper on 2006-08-04
Hi all.
[B]I installed Win4Lin Pro using the --force-architecture command switch and everything seemed to go fine.  Likewise the loading of the Win2K image using the loadwinproCD command.
However, at the nest step to build the Winpro image and make it useable I get the following error:

****buck@Aragorn:~$ /opt/win4linpro/bin/installwinpro

Selected win2kpro to install by default

installwinpro: installation details:
        Target directory: /home/buck/winpro
        Windows version:  win2kpro
        Guest image size: 4G

mergepro-gowimg: created /home/buck/winpro/GUEST.IMG, size=4G
(mergepro-core) /opt/win4linpro/bin/mergepro-gmsg: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory[/B]

I've seen countless messages about a missing libgtk-1.2.so.0 file from /usr/lib, but in my case I HAVE it.  But what I have is a symbolic link to the 64bit library.  It appears that what mergepro wants is a 32bit libgtk-1.2.so.0.  I have installed the i386 libraries listed elsewhere here, but the 32 bit libgtk files don't seem to come with them.
A Synaptic search for libgtk only shows me what I've already got.
Does anyone know how to get the 32bit version of that file installed so it doesn't clobber the 64 bit libs?

---

### Post by Kilz on 2006-08-04
When you are trying to make a 32bit application work, sometimes we have to manualy add 32bit lib's to /usr/lib32. [Here is a howto page I wrote on how to do that.]("http://www.tghc.org/staticpages/index.php/32bitapplications")

---

