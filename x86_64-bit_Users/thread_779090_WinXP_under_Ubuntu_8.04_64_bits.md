---
title: "WinXP under Ubuntu 8.04 64 bits"
date: 2008-05-02
forum: x86 64-bit Users
---

### Post by alexandru_sorin on 2008-05-02
How to run the Winxp under Ubuntu 8.04 64 bits? Don't know what to use for virtual machine. If anyone have an idea ...
System Acer Aspire 5520, 2 Gb Ram, 250 GHdd, AMDTL60 2GHz GeForce 7000M
Everything looks good with ubuntu 8.04. No problem so far.
Thanks,
Alex

---

### Post by ASULutzy on 2008-05-02
I prefer virtualbox.

I think you can just sudo apt-get install virtualbox or sudo apt-get install virtualbox-ose (which is the open source edition)

After that it's just like installing windows normally, pop in the CD, tell the VM to boot off it, install, etc.

---

### Post by alexandru_sorin on 2008-05-05
Thank you.
Alex:

lolflag:

---

### Post by harvey186 on 2008-05-05
If you need USB support, use the deb from the virtualbox webside. The open source version doesn't support USB.

---

### Post by fjgaude on 2008-05-05
If you wish full-featured, except for 3D in WinXP, use this VMware server HOW-TO:

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

It may be a little harder to setup but the overall results will be more pleasing. <smile>

---

### Post by warp99 on 2008-05-05
> **fjgaude said:**
> If you wish full-featured, except for 3D in WinXP, use this VMware server HOW-TO:

[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

It may be a little harder to setup but the overall results will be more pleasing. <smile>

I agree 100%. I use VMware 64bit with a 32bit install of XP without any problems. It's nice to sandbox XP because on my AMD 3200 machine with 2GB of ram the virtual image loads in 15 seconds from power up and that's with SP 2 and virus software.

Also with VMware there are hundreds of virtual appliances to test drive for almost any configuration:

[http://www.vmware.com/appliances/](http://www.vmware.com/appliances/)

---

