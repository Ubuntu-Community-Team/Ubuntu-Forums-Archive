---
title: "Youtube .swf interface freezing"
date: 2008-02-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Fleece Flamingo on 2008-02-18
Is this a known glitch for the 64bit version? If it is only a 64bit problem, how can I force install the 32bit versions of firefox and flash-nonfree?

---

### Post by calman on 2008-02-18
I have the 64 bit version and a lot of other people have it and it works fine...In firefox, if you go to youtube it will ask to install a plugin.  Pick the default one and it should work, if not (this happened to me once) restart firefox and try again, this time it will work.  But you can't install a 32 bit program on a 64 bit machine and OS...you don't want to anyway.

---

### Post by Kilz on 2008-02-18
> **Fleece Flamingo said:**
> Is this a known glitch for the 64bit version? If it is only a 64bit problem, how can I force install the 32bit versions of firefox and flash-nonfree?

Contrary to what is reported above you can [install the 32bit Firefox and plugins.]("http://ubuntuforums.org/showthread.php?t=202537") But first please try the[ r48 flash plugin script ]("http://ubuntuforums.org/showthread.php?t=476924")first. The r115 that is in the repositories is rather buggy.

---

### Post by kwaanens on 2008-02-18
What repo is r115 in? All I get from repos is a non functional r48. The 115 that I have is from the forums.

---

### Post by Kilz on 2008-02-18
> **kwaanens said:**
> What repo is r115 in? All I get from repos is a non functional r48. The 115 that I have is from the forums.

The current flash in the 64bit ubuntu repositories is r115.

---

### Post by kwaanens on 2008-02-18
How is that right for anything but Hardy?
[https://launchpad.net/ubuntu/+source/flashplugin-nonfree](https://launchpad.net/ubuntu/+source/flashplugin-nonfree)

Am I being blind here?

---

### Post by Kilz on 2008-02-18
> **kwaanens said:**
> How is that right for anything but Hardy?
[https://launchpad.net/ubuntu/+source/flashplugin-nonfree](https://launchpad.net/ubuntu/+source/flashplugin-nonfree)

Am I being blind here?

No you are not being blind. But the package name does not reflect the reality of what version is installed. The .deb file does not contain the flash plugin, but downloads it from Adobe. A check of the deb file shows its postinst script  gets the tarball for flash from [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz) . This will download the r115 plugin.

---

### Post by Fleece Flamingo on 2008-02-18
> **Kilz said:**
> Contrary to what is reported above you can [install the 32bit Firefox and plugins.]("http://ubuntuforums.org/showthread.php?t=202537") But first please try the[ r48 flash plugin script ]("http://ubuntuforums.org/showthread.php?t=476924")first. The r115 that is in the repositories is rather buggy.
This was the first thing I did when I installed 64bit version.

---

### Post by Fleece Flamingo on 2008-02-18
I do not know if anything went wrong during the installation but here is the output anyway.
```
pj@pj-desktop:~$ ls -al /usr/lib/mozilla//plugins/
total 8340
drwxr-xr-x 2 pj   users    4096 2008-02-18 17:13 .
drwxr-xr-x 3 root root     4096 2007-10-15 16:27 ..
-rwxr-xr-x 1 pj   users 7040036 2007-06-19 17:31 libflashplayer.so
lrwxrwxrwx 1 pj   users      36 2008-02-15 17:00 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 pj   users      37 2008-02-15 17:00 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 pj   users      34 2008-02-15 17:00 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 pj   users      35 2008-02-15 17:00 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 pj   users      36 2008-02-15 17:00 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 pj   users      37 2008-02-15 17:00 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 pj   users      42 2008-02-15 17:00 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 pj   users      43 2008-02-15 17:00 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 pj   users  286688 2007-08-17 13:21 mplayerplug-in-dvx.so
-rw-r--r-- 1 pj   users    1021 2007-08-17 13:21 mplayerplug-in-dvx.xpt
-rw-r--r-- 1 pj   users  286688 2007-08-17 13:21 mplayerplug-in-qt.so
-rw-r--r-- 1 pj   users    1021 2007-08-17 13:21 mplayerplug-in-qt.xpt
-rw-r--r-- 1 pj   users  286688 2007-08-17 13:21 mplayerplug-in-rm.so
-rw-r--r-- 1 pj   users    1021 2007-08-17 13:21 mplayerplug-in-rm.xpt
-rw-r--r-- 1 pj   users  286680 2007-08-17 13:21 mplayerplug-in.so
-rw-r--r-- 1 pj   users  286688 2007-08-17 13:21 mplayerplug-in-wmp.so
-rw-r--r-- 1 pj   users    1021 2007-08-17 13:21 mplayerplug-in-wmp.xpt
-rw-r--r-- 1 pj   users    1021 2007-08-17 13:21 mplayerplug-in.xpt
lrwxrwxrwx 1 pj   users      60 2008-02-18 17:13 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so
pj@pj-desktop:~$ ls -al /usr/lib/firefox/plugins/
total 24
drwxr-xr-x 2 pj   users  4096 2008-02-18 17:13 .
drwxr-xr-x 5 root root   4096 2008-02-16 08:57 ..
lrwxrwxrwx 1 pj   users    36 2008-02-15 16:59 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 pj   users    37 2008-02-15 16:59 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 pj   users    34 2008-02-15 16:59 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 pj   users    35 2008-02-15 16:59 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 pj   users    36 2008-02-15 16:59 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 pj   users    37 2008-02-15 16:59 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 pj   users    42 2008-02-15 16:59 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 pj   users    43 2008-02-15 16:59 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 pj   users 11456 2008-02-07 03:07 libunixprintplugin.so
lrwxrwxrwx 1 pj   users    43 2008-02-18 15:40 mplayerplug-in-dvx.so -> ../../mozilla/plugins/mplayerplug-in-dvx.so
lrwxrwxrwx 1 pj   users    44 2008-02-18 15:40 mplayerplug-in-dvx.xpt -> ../../mozilla/plugins/mplayerplug-in-dvx.xpt
lrwxrwxrwx 1 pj   users    42 2008-02-18 15:40 mplayerplug-in-qt.so -> ../../mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx 1 pj   users    43 2008-02-18 15:40 mplayerplug-in-qt.xpt -> ../../mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx 1 pj   users    42 2008-02-18 15:40 mplayerplug-in-rm.so -> ../../mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx 1 pj   users    43 2008-02-18 15:40 mplayerplug-in-rm.xpt -> ../../mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx 1 pj   users    39 2008-02-18 15:40 mplayerplug-in.so -> ../../mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx 1 pj   users    43 2008-02-18 15:40 mplayerplug-in-wmp.so -> ../../mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx 1 pj   users    44 2008-02-18 15:40 mplayerplug-in-wmp.xpt -> ../../mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx 1 pj   users    40 2008-02-18 15:40 mplayerplug-in.xpt -> ../../mozilla/plugins/mplayerplug-in.xpt
lrwxrwxrwx 1 pj   users    60 2008-02-18 17:13 npwrapper.libflashplayer.so -> /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so

```

---

### Post by Kilz on 2008-02-18
> **Fleece Flamingo said:**
> I do not know if anything went wrong during the installation but here is the output anyway.


It looks ok, is it still freezing? If so please describe whats going on when it does. Do you have multiple tabs open?

---

### Post by Fleece Flamingo on 2008-02-18
Most of the time I do have multiple tabs. But what happens is when I click something like play once it will not let me re initiate that button to pause the video. I then have to minimize the window and press the button again for it to work.

---

### Post by Fleece Flamingo on 2008-02-20
bump

---

### Post by edantes on 2008-02-20
> **Fleece Flamingo said:**
> Most of the time I do have multiple tabs. But what happens is when I click something like play once it will not let me re initiate that button to pause the video. I then have to minimize the window and press the button again for it to work.

Same here with Firefox/Swiftweasel 2.0.0.12 with Flash 9.0 115. 

But guess what, Firefox 3.0, the latest beta is, if forgive the pun, fireproof.  Four days without a freeze,  and counting.  Even after 10 simultaneous instances of YouTube.  The price to pay is that most of my favorite add-ons are still incompatible.

---

### Post by Fleece Flamingo on 2008-02-23
I installed the Firefox 3 beta but I find the problem to still exist.

---

### Post by Fleece Flamingo on 2008-03-08
any thoughts?

---

