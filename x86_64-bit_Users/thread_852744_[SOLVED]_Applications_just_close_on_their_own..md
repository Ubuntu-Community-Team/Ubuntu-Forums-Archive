---
title: "[SOLVED] Applications just close on their own."
date: 2008-07-07
forum: x86 64-bit Users
---

### Post by onering on 2008-07-07
I'm running Ubuntu 8.04 Hardy Heron 64 bit for about two weeks.  About twice per day an application will just close on it's own.  This has happened to Nautilus, Firefox 3, Blender and other programs.  Ubuntu does not crash, just the application closes. 

I did a RAM test and there were no issues reported.  I was running blender from the command line.  No errors were reported on the command line when it closed.  

Being new to Ubutu Ilinux I'm trying to figure out how to trap the error.  Are there any log files that keep records of what is going on in the system during this event? Any ideas what this could be?  I see a few posts with similar issues on Ubuntu 7.04 but there were no real answers given.

System Setup:
AMD X2 5000+ (No overclocking)
6GB DDR2 RAM: (2+2+1+1)
ASUS AM3 Motherboard
Seagate SATAII 500GB Hard Drive
Dual boot Windows XP 32 and Ubuntu 8.04 Hardy Heron 64 bit 

Thanks.

---

### Post by remu on 2008-07-07
I've had this happen to me too, though I've only experienced this using FireFox, but it happens more than twice a day, its happened twice in the last 5 minutes for me. Some days it never happens, and then others, all the time. I too would like to know whats wrong, and how this could be fixed.

---

### Post by josmcs on 2008-10-05
Did you guys get any reply back on this?  I am having the same problem and haven't been able to find a fix for it.

---

### Post by pablosanchezuy on 2008-10-06
Hi there, i have a lonely post, 

[http://ubuntuforums.org/showthread.php?t=930775](http://ubuntuforums.org/showthread.php?t=930775)

just type one key on any app and it closes.

Go and search your log files for "segfaults", we may have something here.

Regards .

---

### Post by pablosanchezuy on 2008-10-22
Followed this solution, works for me, so far.

[http://ubuntuforums.org/showpost.php?p=5986899&postcount=4](http://ubuntuforums.org/showpost.php?p=5986899&postcount=4)

I took it from post #5 from

[http://ubuntuforums.org/showthread.php?t=949992](http://ubuntuforums.org/showthread.php?t=949992)
Pablo .

---

### Post by lswb on 2008-10-22
The most common cause of a firefox crash is the flash plugin. The latest version 10 final has been working for me for about a week now, Version 9 and the 1st ver 10 beta were also stable on my system but I got crashes with the 1st and 2nd ver 10 release candidates. 

For crashes in general, check you /var/log/syslog and /var/log/Xorg.0.log.old and also make sure you are not running low on free disk space.

---

### Post by pablosanchezuy on 2008-10-29
yes, flash plugin continues to be a pita , but having an unstable system is completely a different thing.

i'm still chasing this matter, because, changing kernel version, dind't last much.

i hope 8.10 with a clean install gets me there, if not, go back to debian.

---

### Post by pablosanchezuy on 2008-11-19
BTW, installed 64bit alpha release from adobe.


NO

MORE

PROBLEMS

.


Go for it.
Pablo

---

### Post by onering on 2008-12-19
> **pablosanchezuy said:**
> BTW, installed 64bit alpha release from adobe.


NO

MORE

PROBLEMS

.


Go for it.
Pablo

Me too!  Installed 64 bit Adobe Flash "alpha" release and all my issues went away!

---

