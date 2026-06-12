---
title: "Ubuntu within OS X"
date: 2005-10-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by noktulo on 2005-10-17
You know how they have [maconlinux]("http://www.maconlinux.org"), where you can run OS X inside of PPC Linux? Is there a way to run Ubuntu within OS X? Kind of like how you can run Windows 98 within Windows XP by using Virtual PC.

---

### Post by bluck on 2005-10-17
[QUOTE=noktulo]You know how they have [maconlinux]("http://www.maconlinux.org"), where you can run OS X inside of PPC Linux? Is there a way to run Ubuntu within OS X? Kind of like how you can run Windows 98 within Windows XP by using Virtual PC.[/QUOTE]

i imagine virtualPC for OS X would do the job.

---

### Post by noktulo on 2005-10-17
Right, but the problem is that emulating the x86 makes it run really slowly. I was looking for something that didn't emulate the processor, so a PPC distro will run quickly.

---

### Post by Joe_lurker on 2005-10-18
If you are looking to run GNU/Linux software you can do it from from OS X.  Look into Fink and Fink Commander - both are available from Apple's software download.  Fink is a Debain-like repository to install OSS apps on OS X.  Fink Commander is a front end to Fink.

-Joe

---

### Post by spoetnik on 2005-10-18
Look into qemu and qemux for free oos emulator. Not fast, but it works mostly.
[http://cordney.com/QemuX/](http://cordney.com/QemuX/)

---

### Post by Rovenhot on 2005-10-18
From what I understand, you have two options:

1. You can emulate the x86 architecture with Virtual PC or QEMU (google for them)  I have used the former, and found that it generally requires a fast computer, e.g. G5 or high-end G4, for decent functionality.  QEMU supposedly runs slower, but might be worth a try, since it's free, and hasn't been bought out by the [COLOR="Blue"]M[/COLOR]on[COLOR="Blue"]$[/COLOR]ter.

2. There is a PowerPC binary of Ubuntu available by download or free-shipped CD.  You can repartition your hard drive (a pain, I know) and install Ubuntu in the new partition, following the guide on the Ubuntu website.  Then, in your Mac OS X System Preferences, you can change the boot drive (Startup Disk) to the Ubuntu partition, and I think there is a mode that allows you to hold the Option key at startup to choose which partition you want to boot from.

---

### Post by calum on 2005-10-18
[QUOTE=noktulo]Right, but the problem is that emulating the x86 makes it run really slowly. I was looking for something that didn't emulate the processor, so a PPC distro will run quickly.[/QUOTE]

[MacOnMac]("http://maconmac.bastix.net/") is what you're looking for, but while Linux support is planned, it doesn't seem to be quite there yet.

---

### Post by Rovenhot on 2005-10-18
Actually, it looks like MacOnMac does support PPC-based Linux distros.  That's probably the best option for Ubuntu-On-Mac.  Thanks, calum

---

### Post by spoetnik on 2005-10-18
Mac-on-Mac looks verry promissing, but doesn't work on OSX higher than 10.3.

---

### Post by Rovenhot on 2005-10-18
Oh, you're right.  The FAQ lists all of its limitations, including the fact that Linux does not have any proper support.

---

