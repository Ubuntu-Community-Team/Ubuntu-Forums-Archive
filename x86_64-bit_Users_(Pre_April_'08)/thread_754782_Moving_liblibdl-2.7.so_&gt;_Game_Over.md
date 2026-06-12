---
title: "Moving /lib/libdl-2.7.so &gt; Game Over"
date: 2008-04-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Thomas_Klaus2 on 2008-04-14
Hello,

i moved /lib/libdl-2.7.so to /libdl-2.7.so. But suddenly nothing worked anymore.bash...
I shutted down the computer then the usual way (Maybe an error).
Using the Ubuntu 7.10 (64) Live CD i moved /libdl-2.7.so to /lib/libdl-2.7.so again.
With no result. Cant start Ubuntu 2.6.22-14 -generic again.

The Ubuntu 2.6.22-14 -generic (recovery) reports now:
error loading /sbin/init no such file or directory ... kernel panic
But wit the live CD /sbin/init seems to be there.

Dont know what to do: Starter Problem.

The reason for moving /lib/libdl-2.7.so:

I had problems with installing 'bless' Hex-Editor.
Required libc6 I took from a deb package.

Then later by installing 'bless' : Broken Package > use sudo apt-get install -f
The result was removing about 10 libs and wine (Working since weeks).
(flashplugin-nonfree not works anymore too, not able to reinstall).

Some bash (Trying to recover):

apt-get install libc6-i386
>
libc6-i386: Depends: libc6 (= 2.6.1-1ubuntu10) but 2.7-10 is to be installed
E: Broken packages

apt-get install libc6
>
libc6 is already the newest version.

apt-get --reinstall install libc6
>
Reinstallation of libc6 is not possible, it cannot be downloaded.

Then I tried the deb - Package for hardy 2.7-10 but the Installer reported:

failed to overwrite /lib/libdl-2.7.so ... broken pipe

So I moved /lib/libdl-2.7.so , see what happens, sorry

And how do I login as the true root on the partition using the live CD?

Thank You.

T_K2

---

### Post by gsmanners on 2008-04-14
Something like this happened in Hardy recently (which I happened to miss, thank goodness).

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-March/000402.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2008-March/000402.html)

---

### Post by Thomas_Klaus2 on 2008-04-14
Seems complicate to find the reasons why the both ways (If it's the right solution for my problem) dont work.

Can you tell me how I can login as "Thomas_Klaus2" to save my recent work, before I 
make a new installation. Without using any deb package (but the apt-get with no critical sources list) again.
(While Installing the maximum Screensize =800x600 that causes that "OK" or "next step"
is often out of screen or unreachable by mouse. And I alvays forget the right Key combination, so I have to try again)...

---

### Post by gsmanners on 2008-04-15
This sort of thing is way beyond my skill level. If it were my system, I would backup my data and reinstall the system.

---

### Post by Thomas_Klaus2 on 2008-04-16
thank you none the less, gsmanners, maybe you'll read my new thread :
[http://ubuntuforums.org/showthread.php?t=757095](http://ubuntuforums.org/showthread.php?t=757095)

I catched my files with explore2fs.exe from the XP partition. Maybe someday
someone will tell me how to login as the true root with the live CD

---

