---
title: "whats a Clam?"
date: 2007-05-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by paulmac on 2007-05-07
Recently upgraded to Fawn, 64 bit.  When getting files from AutomatiX and Synaptic I get a fatal error, something to do with clam.  I did not have this problem with the last version of Ubuntu.  

Ubuntu is FANTASTIC !  I have two Windoze machines, and a Mac.  Ubuntu is more fun.

Don't be too hard on me, not an expert at anything.

paulmac

---

### Post by eyelessfade on 2007-05-07
Need a bit more information to help. What is the whole error message?

clam could be clamav: clamav - antivirus scanner for Unix

---

### Post by paulmac on 2007-05-07
So that what a Clam is!  How long does it take you folks to learn all of these terms?

Here is what I get in AutomatiX " Fatal Error:Brasero   An Apt - Based error occured and inst
was unsuccessful"

In Synaptic    E:clamav: subprocess post-inst. script Returned Error Exit Status 1.

Thanks  paulmac

---

### Post by eyelessfade on 2007-05-07
apt-cache search is your friend :)

try to remove clamav first. Automatix is not supported by the ubuntu team, and its been known to happend that an automatix install can make a lot of problems when upgrading from one release to another. Eg; edgy to feisty.

---

### Post by paulmac on 2007-05-07
apt-cache search is your friend

try to remove clamav first. Automatix is not supported by the ubuntu team, and its been known to happend that an automatix install can make a lot of problems when upgrading from one release to another. Eg; edgy to feisty.

Posted your reply so I wouldn't get lost.  Ok,, I will try to remove clamav (if I can find it).  Too bad about Automatix not being supported, I thought it was very neat.  

I am so very impressed with Ubuntu.  I tried Suse some time ago but could not install anything.  That install process is very hard for an older guy like me that is so used to .exe.
Ubuntu has really changed my opinion of Linux.  KEEP UP THE GOOD WORK!  

I will let you know how it went.

Thanks!

---

### Post by paulmac on 2007-05-07
Hi again

clamav is not installed on my machine but clamav-base is?  No idea what that means.

Thanks

---

### Post by eyelessfade on 2007-05-07
clamav-base - base package for clamav, an anti-virus utility for Unix

do a dpkg -l | grep clamav

that is all packages install on your computer called something with clamav. Remove those, if the problems goes away you can safly install them again if you need a antivirus. Most people dont. only if you need to scan email (server) or a windows partition or similar :)

---

