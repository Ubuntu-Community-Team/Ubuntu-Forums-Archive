---
title: "Ubuntu with Windows"
date: 2006-05-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by higadeb on 2006-05-05
Hi,
   Is there a way that I can have Ubuntu and Windows installed at the same time? I have a live CD but that takes ages to start up and you cant save any work.

Many Thanks
Higadeb

---

### Post by Sef on 2006-05-05
Yes, it is called a dual boot.  Read this excellent tutorial with pictures on how to do it.

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by dsauter on 2006-05-05
Try VMWare Player.  I followed some directions at [http://linux.wolphination.com/?p=18](http://linux.wolphination.com/?p=18) to install Windows 2000 as a "guest" operating system on my home machine.  After that, I used some instructions at [http://www.brandonhutchinson.com/Installing_VMware_Tools_with_VMware_Player.html](http://www.brandonhutchinson.com/Installing_VMware_Tools_with_VMware_Player.html) to get some better integration with my "host" Ubuntu machine (it makes it look and feel like an application, without the <ctrl>-<alt> escape sequence, allowing for cut and paste of text, and a better video driver).  It's networked to the host machine with SAMBA.  It also shuts down by "hibernating" the OS, so when I restart it, it starts far faster than if it was running natively.  The same instructions basically work to make a linux image that can be run on Windows.

It works so well for me that I doubt I will ever dual-boot again.

---

