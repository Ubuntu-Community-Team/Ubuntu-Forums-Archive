---
title: "What Kernel arguement for Breezy installation?"
date: 2006-02-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by spencer on 2006-02-17
Hi,

I'm trying to install breezy on a beige G3 and would like to know what kernel arguement I need to install breezy? I've tried the following "casper/enable=true casper-udeb/snapshot/backing-file=/cdrom/casper/filesystem.cloop" but that only works for the live CD. Where do I find the correct Kernel Arguement for installation?

I can get through part of the installer but it just stops while it tries to load installer components from CD with the following error:

"No kernel modules were found. This probably is due to a mismatch between the kernel used by this version of the installer and the kernel version available in the archive. If you're installing from a mirror, you can work around this problem by choosing to insall a different version of Ubuntu. The install will probably fail to work if you continue without kernel modules."

So, Which ones do I need and where would I find them? Thanks!

-spencer

---

### Post by jdp on 2006-02-17
FWIR of installing on one of my G3MTs (for my guide on Applefritter) you just set the Linux kernel and initrd.gz from the install CD, and leave the rest blank.  It's been a while, but I'm fairly sure that's all you do.  I need to hook up the 8500 I've had sitting around and do another test install on it...

---

### Post by spencer on 2006-02-17
Hi,

I followed the exact steps you provided on the AppleFritter site, and all works up to the point I mentioned and then for some reason stops with the error message and I'm not able to go any further. I have "vmlinux" in Linux Kernels folder and the "initrd.gz" in the system folder. I also leave the Kernel argument line blank in Bootx. Thanks!

-spencer

---

### Post by jdp on 2006-02-18
It sounds as though it's having trouble working with the difference between local vs online versions of the kernel modules.  What version are you installing, and what repositories does it get stuff from?  Is this during the f section of the isntall when you first boot from the CD, or is it later after the reboot?  Also, is this when it's copying file to the HD, or when it's trying to boot from the CD?

---

### Post by spencer on 2006-02-18
The error is during the initial installation while loading components. It just stops and refuses to go any further. It's during the Load installer components from CD section of installation. I never get to the option to choose which disk to install to. As for what version of Ubuntu I'm installing or kernel? It's Breezy and I'm using whatever "vmlinux" kernel in the installation disk. I'll have to reboot again and see which kernel is loading as it passes by so quickly I have trouble reading it. I'll try again. I believe it's version 2.10.6-5.

-spencer

---

### Post by jdp on 2006-02-18
The modules during boot should be a par tof the initrd.gz file.  Did you copy it from the same directory as the kernel?  Is this a burned CD, or a mail-it pressed CD?  If it's burned, did you verify the MD5SUM of the image you downloaded?

---

### Post by spencer on 2006-02-18
Yes. install/powerpc/initrd.gz and install/powerpc/vmlinux.

It is a burned copy of Breezy 5.10 and no I did not verify it, however it did work on my G4 and Pismo. I also have some pressed Hoary CD's I'll try. I believe I did try one and had the same problem. I'll try one again and let you know if that works.

---

### Post by spencer on 2006-02-18
Hi,

Maybe my Burned Breezy CD is Bad and that why all the problems. Don't know.

I used one of my pressed Hoary disks and I got it working. Ubuntu installed perfectly as normal until I get to the (install bootloader) step to hit option-F2. When I hit option-F2 screen goes blank and I don't see any place to type in the commands. I now have Ubuntu installed but have no way to boot it. I'm closer. Thanks!

-spencer

---

### Post by jdp on 2006-02-18
You may need to press "Enter" to start the virtual console after you switch.  Do you have a PCI video card or just the internal?  On my G3MT, it has an ATI card that I used the entire time and no problems.  I haven't tried on the internal video yet.

---

### Post by spencer on 2006-02-18
Not sure if it's PCI or internal. Can I check for it in the system profiler for that? I believe it has a card in it. I'll check. Right now I just finished up another install of Ubuntu and have to come to the boot loader screen. I pressed "Option-F2" followed by "Enter" and still have black(blank screen). So, it's just sitting there at the moment. If I press Option-F1 it takes me back to the ! Continue without boot loader screen. :???: 

-spencer

---

### Post by spencer on 2006-02-18
Hi,

Taken from the System Profiler the display card is: Card name: ATY,mach64_3DU Card model: ATY,GT-B. Is this a problem? Thanks!

-spencer

---

### Post by spencer on 2006-02-19
I've got it working. The solution was to uncheck the no video driver check box in Bootx. I tried installing again with it unchecked and was able to get to terminal and type in commands. The only issue so far is no sound and video is a little garbled in spots. Otherwise Ubuntu works great on the old G3MT. Thanks for all the help jdp! :-D 

Edit: Sorry, I do have sound only while playing xgalaga with "Enable sound server startup" and Sounds for events" unticked. but no sound while Ubuntu is starting up. I'll post some other questions later. Thank you!

-spencer

---

### Post by jdp on 2006-02-19
You're welcome! It good to read that you've solved teh problem, esp with something I'd not have thought to check. :D I had small hope that maybe you were using some strange video card that Ubuntu didn't like, but at least it seems you are running fine.  It's good to ask questions, and better to pass along answers that you know.  That'll keep the community alive more than anything else.

---

