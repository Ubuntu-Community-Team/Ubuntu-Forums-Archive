---
title: "ip1700 printer"
date: 2007-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by Bhawns on 2007-06-06
Ok, so I did the .deb conversion got the ip2200 to show in the install wizard printer is present also it is present on the USB but not printing. It is saying stopped when I check the jobs what is missing? I was getting a report of the pstocanonij not set up in a particular usr/lib directory. could this be the problem? How do I go about solving this problem?

---

### Post by bdoe on 2007-08-26
Figured this would be a good thread to post my problem:

I have a Canon PIXMA iP1700 connected to a Windows XP computer on my network.  It is already set for sharing, and my other Windows clients work well with it.  I would like to be able to connect to it from my Ubuntu laptop.

I did some checking around and learned that there are no Linux drivers for this printer, but the Linux drivers for the iP2200 will work.  So I downloaded the software from Canon's site and unzipped them to my home directory, creating four .RPM files:
cnijfilter-common-2.60-1.i386.rpm
cnijfilter-common-2.60-1.src.rpm
cnijfilter-ip2200-2.60-1.i386.rpm
cnijfilter-ip2200-lprng-2.60-1.i386.rpm

Now here is where my problem is:  When I attempt to use alien to install all of this, it throws more errors than an old WinME system.  Am I taking the right approach with all of this?  What am I doing wrong?

---

