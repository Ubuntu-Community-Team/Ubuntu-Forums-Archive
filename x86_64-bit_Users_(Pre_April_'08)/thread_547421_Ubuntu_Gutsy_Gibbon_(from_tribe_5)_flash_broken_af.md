---
title: "Ubuntu Gutsy Gibbon (from tribe 5) flash broken after update"
date: 2007-09-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by pyrokenx on 2007-09-10
After a recent update I seem totally unable to use any flash, here is the full error that results

```
sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up flashplugin-nonfree (9.0.48.0.0ubuntu8) ...
Installing from local file /var/cache/flashplugin-nonfree/install_flash_player_9_linux.tar.gz
Flash Plugin installed.
/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: error while loading shared libraries: libXcomposite.so.1: cannot open shared object file: No such file or directory
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I've tried alot of things, including using gnash instead and just dealing with it, but then that still doesnt work..

Anyone experience this?

---

### Post by Kilz on 2007-09-10
First off, Gutsy is under development, its in Alpha testing right now. The 64bit section is usualy for released versions. You might want to post problems with Gutsy in its [development Section of the forum.]("http://ubuntuforums.org/forumdisplay.php?f=238")
Second, have you filed a bug report on launchpad regarding this problem? Part of running development versions is reporting bugs so they can be fixed. Posting on the forums is not reporting bugs. Please file a bug report.

---

### Post by pyrokenx on 2007-09-10
well I got gnash working by removing ubufox, flash experiences the exact same problem however.

Gnash can hold me over till someone can help me fix this :)

Dont get me wrong, I WANT gnash to be my new flash, it just doesnt do as much as I want yet, or rather it fails to do more than I can bare at this current moment.  Cant wait till it gets on a comparable level with normal flash

---

### Post by pyrokenx on 2007-09-10
> **Kilz said:**
> First off, Gutsy is under development, its in Alpha testing right now. The 64bit section is usualy for released versions. You might want to post problems with Gutsy in its [development Section of the forum.]("http://ubuntuforums.org/forumdisplay.php?f=238")
Second, have you filed a bug report on launchpad regarding this problem? Part of running development versions is reporting bugs so they can be fixed. Posting on the forums is not reporting bugs. Please file a bug report.

My apologies if this post were misdirected, I will follow this advice from now on in similar situations :)

a moderator may lock or delete this topic as they see fit.  I will go on to post my issue at the development section

---

