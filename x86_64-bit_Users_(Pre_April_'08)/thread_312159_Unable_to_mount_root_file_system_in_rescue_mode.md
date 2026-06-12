---
title: "Unable to mount root file system in rescue mode"
date: 2006-12-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by djp7125 on 2006-12-03
When attempting to mount what was my C drive in Windows using an Ubuntu 6.1 CD in rescue mode, I get the following error message:

Title: [!!] Enter resuce mode
Heading: Mount Failed
Message: An error occurred while mounting the device you entered for your root file system (/dev/hda1) on /target. Please check the syslog for more information.

I am trying to read files off of the hard drive. The system was a Windows XP SP2 with an AMD 64 X2 4600+ with an additional RAID 1 array of 4 SATA drives. Due to a limitation of the on-board Silicon Image RAID controller, I could not boot from the array. So, I installed the aforementioned IDE drive to host the OS. For reasons that still aren't entirely clear, the system blue screened at some point during the night a few days ago stating something to the effect that a needed system file or process was unexpectedly no longer available. When I tried to reboot, it gave me the NTLDR is missing error. I then used my Windows XP install CD to boot to its rescue mode which gave me a command prompt. Issuing the DIR command showed that the windows directory was no longer there. In fact, only 4 directories remained of what was probably more like 12 (from the root) and no root files. The remaining 4 directories were the temp dir, recycle bin, AVG vault and a fourth I can't recall (granted, it's probably irrelevant). Anyways, it seems that most of the drive simply disappeared. Windows was no use at this point so I turned to Ubuntu in the hopes that I could at least recover some of the missing files. However, when booting from the Ubuntu CD, I cannot get past the mounting of the root file system, which is the faulty drive. So, can I still use Ubuntu given my objective? If so, how can I mount this drive? If not, does anyone know of a way to read the drive given its condition (which, admittedly, is partly unknown)? Finally, does anyone know what happened to my drive?

Thanks Ubuntu for the wonderful distro and thanks to ya'll for taking the time.

-Dan

---

### Post by kuja on 2006-12-04
I can think of two things that could have happened to the drive.
a) You were running windows, so it could have been a virus of some sort.
b) Possible though less likely, corruption. Be it the fault of the RAID controller, file system, power outage.... anything really.
c) Other things possible, perhaps, I just can't think of anything else that would be as likely as A.

I'm presuming the whole windows setup is on the RAID right? I hope I'm not wrong anyway.

Mounting it will be somewhat complicated for several reasons:
a) It's probably an NTFS partition, see [this page](https://wiki.kubuntu.org/Kubuntu?action=fullsearch&context=180&value=ntfs&titlesearch=Titles) for dealing with mounting NTFS partitions.
b) It's using a (Fake) RAID controller. You'll need to [install](https://help.ubuntu.com/community/InstallingSoftware?highlight=%28install%29) the dmraid package from the ubuntu [universe repository](https://help.ubuntu.com/community/Repositories). Afterwards, you need to [mount](https://help.ubuntu.com/community/Mount) the partition. The device to be mounted will be found in /dev/mapper/ after installing the dmraid package, assuming it's detected without any issues. For additional information with regards to Fake Raid controllers, and using Ubuntu with them, see [this page](https://help.ubuntu.com/community/FakeRaidHowto).

Also, on a more important note, I recommend running Ubuntu as a live cd while doing your recovery work, it will probably make life easier.
Note: When running it as a live cd, rebooting will lose any customizations/installed packages.

---

