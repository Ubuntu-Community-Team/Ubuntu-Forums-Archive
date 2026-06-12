---
title: "Building AMD64 Rig... parts list included..."
date: 2005-05-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by joekr on 2005-05-12
Hey all,

I'm purchasing the parts to build a new rig tommorow.  The new rig will be replacing my current P4 2.2 Ghz 1GB RAM 660GB HDD (4) running Ubuntu 32.

The parts list is as follows (Canadian prices):

$689  AMD Athlon 64 4000+ 2.4GHz w/1MB L2 Cache Socket 939 (Retail Box)
$110  MSI K8N Neo4-F S.939 nF 4 ATX PCI-E16X/PCI-E1X/PCI-E4X/4PCI 7.1 Ch.
$128  OCZ PC-3200 DDR400 Premier Series 1GB (2x512MB) Dual Channel Kit
$165  Western Digital Caviar SATA (WD2500JD) 250GB 7200RPM 8MB Buffer (OEM)
 CAS2.5 (OCZ4001024PDC-K) (KVR400X64C3AK2/1G)
 Audio,Gb LAN; RAID(0, 1, 0+1); SATA; ATA133
$167  Asus EN6600/TD/128 GeForce 6600 128MB DDR PCI-E w/ TV-Out, DVI
$55   Case
$59   Enermax EG-365P-VE FMA 350 WATT ATX POWER SUPPLY ( TWO FANS w/ MANUAL FAN CONTROL)

I hear that Ubuntu64 *may* still have issues/glitches.  Is this the case?  Would I be better off installing Ubuntu32 like on my P4 machine?

---

### Post by mthaddon on 2005-05-12
There are definitely some hurdles to get over running amd64. Personally I think it's worth it, but you need to be prepared to invest a little more time that on 32bit.

The main thing is that there are some library incompatibilities between 64bit and 32bit which in Ubuntu's case means that to run some applications you will need to set up a 32bit chroot. [Crad's excellent how-to](http://ubuntuforums.org/showthread.php?t=24575)  will help you there. Some examples are Macromedia's Flash Plugin, RealPlayer, Win32codecs. It works well for me with all of these and more, so if you're okay with a little extra time to get everything the way you want it, I'd say go for it! And welcome to the amd64 world!!

---

### Post by AllenGG on 2005-05-12
Hi Joe, my fairly new AMD64 Athlon would only run correctly on Ubuntu 5.04, Tried several other distros, and some M$ stuff for a dual-boot. At this point I have given up on the dual boot idea.
Issues? Glitches? or has Ubuntu (64) spoiled me ?
prices sound a little high,did I misread ?
try : [http://www.filtechcomputer.com/product/default.asp](http://www.filtechcomputer.com/product/default.asp)
beats Tiger Direct

---

### Post by gratefulfrog on 2005-05-25
[QUOTE=joekr]Hey all,
...
I hear that Ubuntu64 *may* still have issues/glitches.  Is this the case?  Would I be better off installing Ubuntu32 like on my P4 machine?[/QUOTE]

It all depends on which apps you want to use. The more demanding they are on the platform, the more likely that they will fail on 64bit. And don't think that the 32bit chroot will make all the problems go away.

If you want easy use, try installing the 32bit Ubuntu.

If you want to help pull the open software world into the future, and aren't afraid of sufffering, then go for the 64bit version.

Beware, that many apps seem to work on 64bit or 32bit chroot, but after extensive use, one discovers that some functions fail, or even worse behave very differently!

Good luck  ;-)

---

### Post by makushimu on 2005-05-25
IMHO, its worth it to at least try 64bit edition out... 
I had doubts myself when I got my AMD64 laptop, and first I ran 32-bit Ubuntu on it, but couple of days ago I decided to give 64bit version a try... and what can i say? I'm happy with it!  \\:D/  
Only problems are with 32bit media apps, but as **mthaddon** pointed out, they can be solved via chroot...

---

