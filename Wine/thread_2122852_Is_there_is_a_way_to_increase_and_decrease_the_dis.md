---
title: "Is there is a way to increase and decrease the disk space in wine?"
date: 2013-03-06
forum: Wine
---

### Post by gregoryshock on 2013-03-06
I am new to using wine.  I tried to install the G2 Real Flight  Simulator.  I was surprised at how easy everything was going.  But then  came the time for it to copy some files from the CD to the hard drive.   It failed and claimed that this could be due to not having enough disk  space.  Does anyone know if there is a way to increase and decrease the  disk space in wine?

---

### Post by Mr. Shannon on 2013-03-06
By default, wine is using you the folder /home/<your user name>/.wine.  So that means that whatever partition your home directory is in is full.  You can run:
```
df -h
```
to find out the space available on your partitions.

---

### Post by gregoryshock on 2013-03-06
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1       109G  5.6G   98G   6% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           780M  932K  779M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  844K  2.0G   1% /run/shm
/dev/sda2       255G   70G  186G  28% /media/6662EAF862EACBBD
/dev/sda1       200M   29M  172M  15% /media/388AED808AED3B50

---

### Post by Mr. Shannon on 2013-03-06
A full drive is clearly not the problem.  Have you tried different windows version modes in wine.  G2 is a very old software, current version is 6.5.  Make sure you are using a 32 bit wine prefix.  Also, sometimes software will just plain refuse to work in wine.  Realflight version G5 demo is the only version that is shown as working on wine at [http://www.winehq.org/](http://www.winehq.org/).

---

### Post by gregoryshock on 2013-03-06
> **Mr. Shannon said:**
> A full drive is clearly not the problem.  Have you tried different windows version modes in wine.  G2 is a very old software, current version is 6.5.  Make sure you are using a 32 bit wine prefix.  Also, sometimes software will just plain refuse to work in wine.  Realflight version G5 demo is the only version that is shown as working on wine at [http://www.winehq.org/](http://www.winehq.org/).

I checked and wine is set to windows xp.  But is it in 32 or 64 bit I have no idea.  Do you know how to tell?

---

### Post by Mr. Shannon on 2013-03-06
Since you did not explicitly set it then it is probably the same as your OS.  Are you running 32 bit or 64 bit ubuntu.  You can tell with:
```
uname -m
```
if this returns x86_64 then your OS is 64 bit and thus wine is probably running in 64 bit mode.  If that is the case you will need to create a new wine prefix with 'win32' as the architecture and install G2 there.

Also, G2 was written for Windows 2000, ME, 98, and 95.  So trying those modes out may help.

---

