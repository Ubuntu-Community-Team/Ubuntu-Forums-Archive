---
title: "PowerMac 8500 - Black screen all around..."
date: 2005-10-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Appleguy2004 on 2005-10-14
Hi guys, I've been trying, unsuccessfully, for two days to install Breezy on my PM8500, I'm a Linux noob, outside of some fiddling with the OS X Terminal on my iBook.

Here is my setup: 2 SCSI hard drives, one 2GB and the other 4GB. I'm installing on the 4GB, 100MB HFS+ partition for a minimal Mac OS containing BootX, and the rest unallocated for Breezy. The video card is the default that came with the computer (ATI).

My problem is that everytime I cannot get anything but a black screen when inside terminal. If I uncheck "No video driver" in BootX, I get a kernel panic error. So I always leave that checked, but that means that, following Jon's instructions on this thread ([http://www.applefritter.com/node/8936)](http://www.applefritter.com/node/8936)), when I press Opt. F2 in the installer, I get that black screen again, and I can't do anything at all.....

Is there any way to get video working on this (admitedly old) machine? I would appreciate insightful advice and any form of Linux voodoo that would point me in the right direction! Cheers! :p

---

### Post by ssam on 2005-10-14
for an old-world machine you may have more luck with yellowdog linux. maybe once you have got that working you'd be able to install ubuntu.

---

### Post by Appleguy2004 on 2005-10-14
I have thought of installing YDL, but it seems like Ubuntu was a better distro. Besides. technically, wouldn't I still have the same problem once I would try to boot into any terminal, wether it be YDL or Ubuntu?

I have tried entering "video=ofonly:vmode:17:cmode:16" as a kernel argument in BootX, but with no effect whatsoever...

---

### Post by tonyB on 2005-10-17
My system (7300 upgrade to 7500) is similar to yours, and I seem to recall having a problem like this when i installed warty.  unfortunately, I cannot recall the details that far back -- due to brain-stem rot no doubt.  I think the problem was related to boot parameters, but I'm not sure.  I have breezy partially installed (I'm having different problems) and what I did:

cp vmlinux and initrd.gz from install cd to Linux Kernels folder in System folder on mac.

reboot system into bootX.  For me running bootX from mac os does not work.

in bootX select vmlinux; in options check use ramdisk and select initrd.gz from Linux Kernels folder.

the kernel parameters box is empty.

If this is what you did then it's something else.  You might try increasing the size parameter from 8K to 32000.  I didn't have to, but with warty I did.

Sorry, I cannot recall anything else.

good luck,
tony

---

### Post by ylo on 2005-10-20
Hi, the following link addresses the problems on Open Firmware 1.0.5 machines that use output-device /chaos/control (i.e. PowerMacintosh 7300 - 8600).

[http://www.netbsd.org/Ports/macppc/SystemDisk-tutorial/of105patch.html](http://www.netbsd.org/Ports/macppc/SystemDisk-tutorial/of105patch.html)

Please let me know what if any effect this has on your problem ( i've got an 8500/ppc still my self, haven't tried linux or bsd on it since linuxPPC 2000 tho ). Nice hardware :) i miss the beige apple days ( *sigh* ). 

Cheers:
yello

---

### Post by The Rev on 2005-10-22
Hi,

I face the same problems Appleguy2004 has. I was able to install Kinux on my hd, used bootx and followed all the instrucions. By the the time I had to switch to another terminal (option-F2) I saw the same black screen. Then I finisfehd installation. Reboot system and saw bootx again with the choice linux/OS9. Entering Linux brought me to a new installation, OS9, no problems. I have to reconfigure bootx (I think) but how and with what parameters. Does anybody know?:confused:

---

