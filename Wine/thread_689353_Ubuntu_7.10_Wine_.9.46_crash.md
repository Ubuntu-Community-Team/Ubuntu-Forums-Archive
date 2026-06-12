---
title: "Ubuntu 7.10 Wine .9.46 crash"
date: 2008-02-06
forum: Wine
---

### Post by messatsu on 2008-02-06
Ubuntu 7.10 (fresh install yesterday, downloaded yesterday)
Wine 9.46

Sempron 2600
HDD is partitioned with XP NTFS first and ext3 for Linux
(will give more hardware information if relevant)

Everytime I use any Wine application (I'm just trying to load the config at this point), Wine locks the OS up.  I get no flashing from the HDD light, I lose mouse control, and when I tried in the terminal, the cursor didn't blink and ctrl+C is unresponsive and probably the entire keyboard.  The last thing on screen of the terminal is:
```
$sudo winecfg
wine: creating configuration directory 'home/<username>/.wine'...
```

Listing of that directory, the two reg files are last created of those.
```
$ ls -lR
.:
total 24
drwxr-xr-x 2 root root 4096 2008-02-06 09:57 dosdevices
drwxr-xr-x 3 root root 4096 2008-02-06 09:57 drive_c
-rw-r--r-- 1 root root 7574 2008-02-06 09:58 system.reg
-rw-r--r-- 1 root root 7718 2008-02-06 09:58 user.reg

./dosdevices:
total 0
lrwxrwxrwx 1 root root 10 2008-02-06 09:57 c: -> ../drive_c
lrwxrwxrwx 1 root root  1 2008-02-06 09:57 z: -> /

./drive_c:
total 4
drwxr-xr-x 8 root root 4096 2008-02-06 09:57 windows

./drive_c/windows:
total 28
drwxr-xr-x 2 root root 4096 2008-02-06 09:57 command
drwxr-xr-x 2 root root 4096 2008-02-06 09:57 fonts
drwxr-xr-x 2 root root 4096 2008-02-06 09:57 inf
drwxr-xr-x 2 root root 4096 2008-02-06 09:57 system
drwxr-xr-x 4 root root 4096 2008-02-06 09:57 system32
drwxr-xr-x 2 root root 4096 2008-02-06 09:57 temp
-rw-r--r-- 1 root root  617 2008-02-06 09:57 win.ini

./drive_c/windows/command:
total 0

./drive_c/windows/fonts:
total 0

./drive_c/windows/inf:
total 176
-rw-r--r-- 1 root root 173923 2008-02-06 09:57 wine.inf

./drive_c/windows/system:
total 0

./drive_c/windows/system32:
total 8
drwxr-xr-x 2 root root 4096 2008-02-06 09:57 drivers
drwxr-xr-x 3 root root 4096 2008-02-06 09:57 spool

./drive_c/windows/system32/drivers:
total 0

./drive_c/windows/system32/spool:
total 4
drwxr-xr-x 2 root root 4096 2008-02-06 09:57 drivers

./drive_c/windows/system32/spool/drivers:
total 0

./drive_c/windows/temp:
total 0

```
I installed first via Ubuntu's GUI package manager and later via Synaptic and no luck.

---

### Post by happyhamster on 2008-02-06
Well, there are a few threads in this forum about wine-crashes (most problems caused by specific chipset/sound/video hardware it seems), but what you should try first is running wine as a regular user. Don't run wine as root (by using 'sudo'). That goes for all things wine-related, including winecfg.

Is the hidden .wine folder currently located in your home dir? In that case, it's probably enough to manually delete it. Then create a fresh one by running

winecfg

again (without sudo).

---

### Post by messatsu on 2008-02-06
There are three .wine folders in my home directory.  Each one was created from my attempt to run anything.  They all start as ".wine-******".  I'll try again without sudo and deleting the existing .wine folders, but the first two tries were from the GUI which would be without any su permissions. :/  If that doesn't work, I'll search my specific hardware and go from there.  Thanks.

---

### Post by messatsu on 2008-02-06
Seems you're right about the hardware, though nothing of mine has popped up in searches [http://ubuntuforums.org/showthread.php?t=426900](http://ubuntuforums.org/showthread.php?t=426900)  It's nice to know others are having the same problem.

---

