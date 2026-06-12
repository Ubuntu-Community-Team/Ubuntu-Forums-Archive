---
title: "dual boot"
date: 2005-12-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by drhedberg on 2005-12-26
I am currently running panther on an iBook G3.  Can I install ubuntu and dual boot without it affecting my current data/files etc in OS X?  

Thanks for your help

---

### Post by tmeier on 2005-12-26
The easiest way I know to make this happen is using Carbon Copy Cloner and a second hard drive in your case would have to be an external hard drive like an ipod.  I have a powerbook G4 and did the following process.

1.  Downloaded Carbon Copy Cloner from [http://www.bombich.com](http://www.bombich.com).

2.  Connected my ipod(external harddrive) to my computer and used Carbon Copy Cloner to make a backup of my current system.  This will make a complete backup of your harddrive and will make it bootable also.  Make sure this works so that when you restore it you have a working copy of your original setup.

3.  I then booted my powerbook from my ipod and used Disk utility and repartitioned my hard drive.  I made one partition for os X and formatted it as hfs+.  I made a second partition for Ubuntu and did not format it.  I left it as free space.  (If you do a search in this forum I think OS X needs to be in the second of the 2 partitions you make but search here to find out for sure).

4.  I used Carbon Copy Cloner to copy my system from my ipod/external hard drive back to the OS X partition on my system.  I booted this up to make sure it worked and everything was found.

5.  I stuck in my Ubuntu CD and installed it letting the installer do my formating of the free space for me.  It installed Ubuntu without any problems.  

6.  When it restarted I had the option of booting to Linux or to OS X.  My system works great, I just wish I had given more space to Ubuntu and less for OS X.  

Still findng things that I need to fix, but am getting closer of not needing OS X anymore.   I hope this helps and if I left anything out hopefully someone will chime in and correct me.

---

### Post by drhedberg on 2005-12-26
Thank you for this comprehensive reply.  I have an iPod so I'll give it a shot.

---

