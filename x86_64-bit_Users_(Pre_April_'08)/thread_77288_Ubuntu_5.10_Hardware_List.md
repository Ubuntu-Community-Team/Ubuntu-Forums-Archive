---
title: "Ubuntu 5.10 Hardware List"
date: 2005-10-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Aphorism on 2005-10-16
I think it would be prudent to offer up a hardware list for those folks who wish to run an Ubuntu system with ease in mind.  My experience was just plain awful, so I am hoping we can maybe contribute some details for hardware that actually works *well*.  I'll start:

**SPECS:**
MSI-RS480M2 motherboard.  mATX form factor (which is why I chose it).

**ISSUES:**
[LIST]
[*]/etc/X11/xorg.conf would lynch the system.  By default, Ubuntu successfully detected the onboard ATI graphics chip, but the xorg ati driver will not work out of box without the no accelleration option.  If you flip the driver over to vesa, all works great minus the 3d/2d accelleration.  Of course, we have ATI to thank for that.
[*]There are apparent sata issues if you try to boot off of a sata drive.  I haven't yet, so I can't provide extensive details on it.
[*]Clock skew.  Your clock will run at double speed unless you specify in grub no_timer_check after the kernel parameter.  More ATI stuff.
[/LIST]

**VERDICT:**
I hate ATI now.  I will never buy another one of their products.  I cannot recommend this board, even though I have it currently working and stable.  It is a pain and you shouldn't need to jump through so many hoops.

Thumbs DOWN.

---

### Post by bonzodog on 2005-10-16
I've found one of the ways to ensure that your hardware just works with most distro's  is to buy nvidia based gear - it nearly always works. My system did just that- it Just Worked.
specs;
MSI K8N NeoPlatinum Nforce3 mobo with on-board sound (nvidia CK8S), GBLan.
GeForce 6200 256MB Graphics card.
1GB Ram
160GB IDE HDD
AMD64 3000+ CPU
17" TFT Samsung SyncMaster 710v Monitor
DSL Router plugged into Ethernet
Epson R200 USB printer

---

### Post by ikd69 on 2005-10-16
amd64 3000+
ASUS A8N SLI
200 GB Seagate SATA
ATI X700

I have already replaced the disk 3 times (the folks at the local store must hate me for this :smile: ) but that was due to a faulty mobo which was also changed.

Did not have any troubles installing either gentoo or 5.04 and now 5.10, although grub complained and got stuck when either the "/" or the "/home" partition was over 100G --- don't know why.

Vesa sucks but if you follow the instructions for installing the driver for ati, it works just fine.

Cheers,

ikd

---

### Post by kellyhardinguk on 2005-12-15
I installed Breezy on my Socket 754 Athlon64 system.

Had no problems with it at all really. Even with the SATA drives/controllers.

System:

Socket 754 Athlon64 3000+
1Gb PC3200 RAM
MSI K8T Neo (with via and promise SATA/PATA RAID)
80Gb Seagate SATA hard drive, 200Gb Seagate SATA hard drive.
Nvidia Geforce 6600GT AGP
21" Cornerstone P1500 CRT

Ubuntu installed fine onto the space I'd left on the 80Gb drive after installing XP Pro on the drive (used NTFS for it). All installed well. No problems on booting.

All booted up into Ubuntu fine. All seems to work.

I've not yet gotten round to getting the nvidia drivers installed as I've had trouble with the system today unrelated to Ubuntu itself.

The X settings weren't right, I had to manually set them up myself. But this has been the case of all Linux distros tried with that monitor. Seems only Mac OS X can manage to get it right, Windows XP doesn't even manage it.

(I share the CRT and USB keyboard/mouse via a KVM between this PC and a Apple PowerMac G3 running OS X)

Kelly

---

