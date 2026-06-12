---
title: "Realplayer on AMD64"
date: 2005-03-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by mthaddon on 2005-03-23
Just like to see if anyone's resolved this issue on Hoary? Can't get Realplayer working on AMD64

[http://ubuntuforums.org/showthread.php?t=599&highlight=amd64+realplayer](http://ubuntuforums.org/showthread.php?t=599&highlight=amd64+realplayer)

Thanks, Tom

---

### Post by X3N on 2005-04-03
I've not been able to install it, though i've only been running hoary (64) for a couple of days, but a work around that might be worth exploring is using mplayer [or any other client?] that will use the RealMedia codecs that are in the win32codec pack.

---

### Post by mthaddon on 2005-04-04
So I guess that brings up another issue - how did you install the win32codecs? 32-bit chroot? I've been thinking that's the only way to do it, but haven't yet had time to go down that path.

Thanks, Tom.

---

### Post by dewey on 2005-04-05
Yes, the only way to run 32-bit anything is within a chroot environment.  And there has yet to be any win32codec port for 64bit, along with a few other things, like flash. (Although flash has many projects working on getting it there)

---

### Post by wmcbrine on 2005-04-06
[QUOTE=dewey]Yes, the only way to run 32-bit anything is within a chroot environment.[/QUOTE]
No, most stuff will work with just what's in */lib32. But not this, I guess.

---

### Post by dmatrix on 2005-04-06
Correct must stuff does work with /usr/lib32. RealPlayer, w32codecs and Flash plugin are another story though.

---

### Post by arunsub on 2005-04-25
I'm a newbie. What's chroot environment?

---

### Post by Ephack on 2005-04-25
A chroot environment enables you to execute some applications in a new environment without having to reboot your system. Typically, it is usefull if you're running a 64bits environment and want to execute an application that is not available for this architecture. The chroot environment is then a basic 32bits environment. See this post for more practical informations:
[http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)

---

