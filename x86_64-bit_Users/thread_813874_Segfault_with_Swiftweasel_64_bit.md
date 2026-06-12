---
title: "Segfault with Swiftweasel 64 bit"
date: 2008-05-31
forum: x86 64-bit Users
---

### Post by stephenb on 2008-05-31
After being frustrated at not getting flash working with firefox I decided to install Swiftweasel, using this package: 

[INDENT]swiftweasel32-2.0.0.14_athlon64-32bit_ubuntu_7.10-8.04_AMD64.deb
[/INDENT]
After installed, when I tried to run it I get this:

[INDENT]swiftweasel-bin[6186]: segfault at 0 rip 0 rsp ffbe4830 error 14
[/INDENT]
Has anyone had the same problem? Any suggestions?

Please note that I have been getting a series of segfaults (wine, skype, npviewer, nautilus, gtk-gnash) since upgrading to Hardy from Feisty. Some have meant programs simply will not run.

---

### Post by Kilz on 2008-06-02
> **stephenb said:**
> After being frustrated at not getting flash working with firefox I decided to install Swiftweasel, using this package: 

[INDENT]swiftweasel32-2.0.0.14_athlon64-32bit_ubuntu_7.10-8.04_AMD64.deb
[/INDENT]
After installed, when I tried to run it I get this:

[INDENT]swiftweasel-bin[6186]: segfault at 0 rip 0 rsp ffbe4830 error 14
[/INDENT]
Has anyone had the same problem? Any suggestions?

Please note that I have been getting a series of segfaults (wine, skype, npviewer, nautilus, gtk-gnash) since upgrading to Hardy from Feisty. Some have meant programs simply will not run.

The package you installed is a 32bit version of Swiftweasel in a 64bit package. You have a seriously fubar'd system if 32bit applications are seg faulting. what does 
```

ls -al /usr
```
return

My personal advice is do a clean install to avoid all the problems you have reported.

---

### Post by stephenb on 2008-06-02
> **Kilz said:**
> You have a seriously fubar'd system if 32bit applications are seg faulting.

Yep, something does seem to be amiss all right ...

Here is the output for ls -al /usr:
total 316
drwxr-xr-x  14 root root   4096 2008-05-31 10:53 .
drwxr-xr-x  21 root root   4096 2008-06-03 07:57 ..
drwxr-xr-x   2 root root  73728 2008-06-03 07:57 bin
drwxr-xr-x   2 root root   4096 2008-05-09 17:59 games
drwxr-xr-x  71 root root  12288 2008-06-01 14:36 include
drwxr-xr-x 248 root root 110592 2008-06-02 23:26 lib
drwxr-xr-x  36 root root  36864 2008-06-01 14:49 lib32
lrwxrwxrwx   1 root root      3 2007-02-03 23:36 lib64 -> lib
drwxr-xr-x  15 root root   4096 2008-05-31 12:33 local
drwx------   2 root root  16384 2007-02-03 23:34 lost+found
drwxr-xr-x   2 root root  20480 2008-06-02 07:46 sbin
drwxr-xr-x 432 root root  16384 2008-06-01 14:42 share
drwxr-xr-x   3 root root   4096 2008-05-07 09:15 shareFeisty
drwxrwsr-x  14 root src    4096 2008-06-01 14:42 src
drwxr-xr-x   4 root root   4096 2007-02-03 22:01 X11R6

> **Kilz said:**
> My personal advice is do a clean install to avoid all the problems you have reported. 

Sigh. I think you might be right. 

But I'm running a little web server, so I'll have to look into how to do a clean install as painlessly as possible. I'm dreading the thought of the time it will take to set everything up again.

---

