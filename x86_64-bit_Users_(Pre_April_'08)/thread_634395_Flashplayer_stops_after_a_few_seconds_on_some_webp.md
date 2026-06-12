---
title: "Flashplayer stops after a few seconds on some webpages"
date: 2007-12-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by dandandan on 2007-12-07
Hello

My ff+flashplugin-nonfree stop working after a few seconds on some flash websites.
First it works normally, but after 5-30 seconds, firefox windows just goes grey and nothing more is displayed.
Websites that show this kind of behaviour each visit are for example:
[www.war-europe.com](www.war-europe.com) or [www.burgerking.at](www.burgerking.at).

Anybody knows this behaviour or knows how to fix this?

mfg
dan

---

### Post by dandandan on 2007-12-14
*bump*

After a few seconds till one minute of working fine it then looks like that:


[http://img85.imageshack.us/img85/9497/screenshotbu7.png](http://img85.imageshack.us/img85/9497/screenshotbu7.png)

or:

[http://img135.imageshack.us/img135/5583/screenshot1zd8.png](http://img135.imageshack.us/img135/5583/screenshot1zd8.png)

---

### Post by fjgaude on 2007-12-14
I let the Burger King site run for about a minute without any issues, using 64-bit Ubuntu and Epiphany browser... fast action, movement. All okay.

Sorry I have no thoughts about what could be wrong with your setup.

---

### Post by Kilz on 2007-12-14
> **dandandan said:**
> *bump*

After a few seconds till one minute of working fine it then looks like that:


[http://img85.imageshack.us/img85/9497/screenshotbu7.png](http://img85.imageshack.us/img85/9497/screenshotbu7.png)

or:

[http://img135.imageshack.us/img135/5583/screenshot1zd8.png](http://img135.imageshack.us/img135/5583/screenshot1zd8.png)

How many different ways have you tried to install flash?

Please give us the results of 
```
ls -al /usr/lib/mozilla/plugins
```

---

### Post by dandandan on 2007-12-14
i installed it via apt-get, but since the package is broken, i commented out the stuff in the post.inst, relating to the md5 sum.
after that didn´t work i ran over ith with nswrapper thingi with -i param and then with -i -a -v param
all resulting in the same.
result of the ls is 

 ls -al /usr/lib/mozilla/plugins
total 1448
drwxr-xr-x 2 root root   4096 2007-12-08 03:40 .
drwxr-xr-x 3 root root   4096 2007-10-16 01:27 ..
lrwxrwxrwx 1 root root     37 2007-12-08 03:40 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root     36 2007-12-05 16:44 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root     37 2007-12-05 16:44 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root     34 2007-12-05 16:44 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root     35 2007-12-05 16:44 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root     36 2007-12-05 16:44 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root     37 2007-12-05 16:44 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root     42 2007-12-05 16:44 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root     43 2007-12-05 16:44 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 286688 2007-08-17 22:21 mplayerplug-in-dvx.so
-rw-r--r-- 1 root root   1021 2007-08-17 22:21 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 root root 286688 2007-08-17 22:21 mplayerplug-in-qt.so
-rw-r--r-- 1 root root   1021 2007-08-17 22:21 mplayerplug-in-qt.xpt
-rw-r--r-- 1 root root 286688 2007-08-17 22:21 mplayerplug-in-rm.so
-rw-r--r-- 1 root root   1021 2007-08-17 22:21 mplayerplug-in-rm.xpt
-rw-r--r-- 1 root root 286680 2007-08-17 22:21 mplayerplug-in.so
-rw-r--r-- 1 root root 286688 2007-08-17 22:21 mplayerplug-in-wmp.so
-rw-r--r-- 1 root root   1021 2007-08-17 22:21 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 root root   1021 2007-08-17 22:21 mplayerplug-in.xpt

and the symlink pointing on that
 ls -al /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root 56 2007-12-08 03:40 /etc/alternatives/mozilla-flashplugin -> /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so

---

### Post by fjgaude on 2007-12-14
Gosh, mine is very simple and it works on everything I've tried it with, using both Firefox and Epiphany:

```
frank@sunshine:~$ ls -al /usr/lib/mozilla/plugins
total 8
drwxr-xr-x 2 root root 4096 2007-12-11 11:06 .
drwxr-xr-x 3 root root 4096 2007-10-15 16:27 ..
lrwxrwxrwx 1 root root   37 2007-11-23 17:49 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root   26 2007-12-11 10:53 gxineplugin.so -> ../../gxine/gxineplugin.so
lrwxrwxrwx 1 root root   31 2007-12-11 11:06 xineplugin.so -> ../../xine-plugin/xineplugin.so
```

I wonder if I should uninstall the gxineplugin.so?

---

### Post by dandandan on 2007-12-17
*push*

anyone, this bug is getting annoying but since it doenst happen to all, it may be configuration issue.

---

### Post by Kilz on 2007-12-17
> **dandandan said:**
> i installed it via apt-get, but since the package is broken, i commented out the stuff in the post.inst, relating to the md5 sum.
after that didn´t work i ran over ith with nswrapper thingi with -i param and then with -i -a -v param
all resulting in the same.
result of the ls is 

 ls -al /usr/lib/mozilla/plugins
total 1448
drwxr-xr-x 2 root root   4096 2007-12-08 03:40 .
drwxr-xr-x 3 root root   4096 2007-10-16 01:27 ..
lrwxrwxrwx 1 root root     37 2007-12-08 03:40 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root     36 2007-12-05 16:44 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root     37 2007-12-05 16:44 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root     34 2007-12-05 16:44 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root     35 2007-12-05 16:44 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root     36 2007-12-05 16:44 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root     37 2007-12-05 16:44 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root     42 2007-12-05 16:44 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root     43 2007-12-05 16:44 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 286688 2007-08-17 22:21 mplayerplug-in-dvx.so
-rw-r--r-- 1 root root   1021 2007-08-17 22:21 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 root root 286688 2007-08-17 22:21 mplayerplug-in-qt.so
-rw-r--r-- 1 root root   1021 2007-08-17 22:21 mplayerplug-in-qt.xpt
-rw-r--r-- 1 root root 286688 2007-08-17 22:21 mplayerplug-in-rm.so
-rw-r--r-- 1 root root   1021 2007-08-17 22:21 mplayerplug-in-rm.xpt
-rw-r--r-- 1 root root 286680 2007-08-17 22:21 mplayerplug-in.so
-rw-r--r-- 1 root root 286688 2007-08-17 22:21 mplayerplug-in-wmp.so
-rw-r--r-- 1 root root   1021 2007-08-17 22:21 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 root root   1021 2007-08-17 22:21 mplayerplug-in.xpt

and the symlink pointing on that
 ls -al /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root 56 2007-12-08 03:40 /etc/alternatives/mozilla-flashplugin -> /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so

That is indeed a weird setup (symlink redirecting to symlink), but it should work, I see no conflicts, which is usually the case.

---

### Post by Berto on 2007-12-19
dan, I have the same issue.

Check out the discussion here:
[http://ubuntuforums.org/showthread.php?t=642818&highlight=flash](http://ubuntuforums.org/showthread.php?t=642818&highlight=flash)

My issues started when Ubuntu updated my libflashplayer-nonfree.  I'm now using the r48 archive and if it doesn't work, I'll go down to r47, and so on.

I stole the commands from this script:
[http://ubuntuforums.org/showthread.php?t=476924&highlight=flash](http://ubuntuforums.org/showthread.php?t=476924&highlight=flash)

but didn't use the script since it'll download the new version which is killing me.

---

### Post by dandandan on 2007-12-20
thanks Berto you are a lifesaver.
I downloaded the old Version and it works perfectly, again big thanks.

---

### Post by Berto on 2008-01-06
No problem Dan - I just had to come re-find my post as I've installed a new system and have the same problem in 64-bit with the latest version.  Back to r48 for me.

---

