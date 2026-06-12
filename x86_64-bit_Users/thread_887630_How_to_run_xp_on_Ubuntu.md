---
title: "How to run xp on Ubuntu"
date: 2008-08-12
forum: x86 64-bit Users
---

### Post by kyo007 on 2008-08-12
hi, can i run xp on ubuntu ? I have 2 disk, one for linux x64 other for windows xp x64, i want to run windows when i am working on ubuntu, is it possible ?

Thx.

---

### Post by dje on 2008-08-12
yes using virtualisation software like VirtualBox, have a look [here]("http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html")

EDIT: VirtualBox does not currently support 64 bit guest operating systems

VMware server 2.0 supports 64 bit guests, download [here]("http://www.vmware.com/beta/server/index.html")

dje

---

### Post by kyo007 on 2008-08-12
so can i run xp witout re-install it ?

---

### Post by houbysoft.xf.cz on 2008-08-12
I don't know what you mean exactly, but I guess not. You must install XP on a virtual drive if you want to run it when you're on Ubuntu.

---

### Post by dje on 2008-08-12
yes you must install vmware server, then launch it and create a new virtual machine. start the virtual machine and install windows as normal using your install disc. remember that you must have a reasonably powerful system (1gb ram preferably dual core) to run smoothly with two operating systems running at once

dje

---

### Post by tuxxy on 2008-08-12
[https://help.ubuntu.com/community/VMware](https://help.ubuntu.com/community/VMware)

---

### Post by xinix on 2008-08-12
It is possible to run your currently installed xp64 installation.  I've just started to get mine to work.  X64 has an issue with drivers for SCSI drives, and the kernel treats IDE drives as SCSI (because it gives better performance than PATA).  I say this because it was my biggest hurdle in the process.  I kept encountering BSOD at boot.  The most frustrating thing was that my XP drive was an IDE and not SCSI.  This was not an issue when I tested with a virtual disk, just using the existing install.

I used these links to get me started:
both of these are fairly similar
[http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu]("http://www.squidoo.com/use-existing-windows-installation-and-apps-in-ubuntu")

[http://venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/]("http://venturecake.com/a-simple-guide-to-using-your-existing-windows-install-apps-in-ubuntu/")

This had the answer to my BSOD at Boot problem:
[http://http://communities.vmware.com/thread/21909;jsessionid=E612C27DC695F1846D8ABE304F124B1D?tstart=0&start=15]("http://communities.vmware.com/thread/21909;jsessionid=E612C27DC695F1846D8ABE304F124B1D?tstart=0&start=15")


Then there is another biggie called Windows Activation.  I found the solution to this.  I haven't tried the script on the page but manually copying the files does work.  Here's the link:
[http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/]("http://mazimi.wordpress.com/2007/07/11/getting-around-windows-activation-when-virtualizing/")

Now I've just gotta get netflix watch it now working.  I think it's solvable but at the moment it's very choppy.

---

### Post by Flag on 2008-08-14
If I understand you well, you've two physical drives, on one of them WS on the other Linux, if that's the case the only thing you need to do is adjust you boot options.
Software like "  supergrub " will do the thing for you, also check out " how to grub "

---

### Post by Jouke74 on 2008-08-14
No he wants to run XP from **within** Ubuntu. The only way to do that is indeed with virtualization. See previous posts for solution.

And yes, you need to reinstall windows Xp, because the hardware of the virtual machine for sure does not match your own hardware. The good news is that you do not need to install much more afterwards (like drivers) to get everything running. Learn about Vmware, Virtualbox, or even Kvm (last one is the standard virtualization tool of the kernel, it's running fast but hard to learn).

---

