---
title: "Ubuntu 7.10-AMD64 LTSP  How do I install???"
date: 2007-12-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by jpaulb on 2007-12-27
I have been using LTSP on Debian for a couple of years, I thought of switching to Ubuntu 7.10

I have installed the package  server stand alone 5.0.39, however I am at a lost to get it running. Is there any Howto for the Ubuntu 7.10 AMD64 installation? Everything I have seen so far is for the i386. They mentions file like" nbi.img"  that to not exist

The thin client stops after client IP  and DHCP IP  are found with a warning 
 TFTP open time out.


thanks

Paul

---

### Post by sudev on 2008-01-11
The version to be installed depends on the client hardware. I am using amd64 for my laptop but have installed i386 architecture for the thin clients by
 
$ sudo ltsp-build-clients --arch i386

If you do not give --arch the default is to assume same architecture as host. You can also do --arch ppc (I think) for apple clients.

---

### Post by jpaulb on 2008-01-11
Thanks a lot.
I never saw any referral to that.

I have noted that, so if I try Ubuntu again I can get the LTSP working and maybe not give up muttering andreinstall Debian

---

