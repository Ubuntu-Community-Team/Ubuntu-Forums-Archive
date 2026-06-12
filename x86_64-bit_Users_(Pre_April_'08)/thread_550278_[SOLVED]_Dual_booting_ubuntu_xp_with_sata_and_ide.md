---
title: "[SOLVED] Dual booting ubuntu xp with sata and ide"
date: 2007-09-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by YoshiHNS on 2007-09-13
After my first attempt to repair my first installation failed, i decided to take a second stab and document all the steps in case it worked to other people trying to do the same thing could see how it can be done.

The situation is thus. I have one sata drive with windows xp installed. The entire drive was partitioned as ntfs. I used the partition manager on the ubuntu live cd to shrink the main partition and create the other necessary partitions for ubuntu in the newly created space. I have left the partitions alone since i deleted ubuntu to start over since the partitions are fine and caused me no trouble. To begin i will run mbrfix to make sure that my MBR is clean. Then i will use Partition Magic to delete the swap partition and all other partitions besides my windows partition. I will then reinstall ubuntu in the unpartitioned area of my sata drive using the live cd 7.04 x64.

---

### Post by YoshiHNS on 2007-09-13
OK. Attempt one failed. I started with a fresh MBR. Booted on the live cd, installed ubuntu. I used the manual partition option, created a one gig swap and the rest as my root. I also clicked on the advance button and changed boot location from drive 0 to drive 1, since my sata drive would be recognized at drive 1. After the install, i restarted, grub loaded with correct selections, and all os choices returned an error 22: partition does not exist. I am going to try and see if i can fix grub and this error.

---

### Post by YoshiHNS on 2007-09-14
ok, i have tried multiple things to fix this. i started with the bios, changing boot orders,  changing hd boot order. nothing worked. i tried editing grub with all sorts of fixes, and none of that work. Im going to try again with the ide drive disconnected.

---

### Post by YoshiHNS on 2007-09-14
very interesting, how using fixmbr from the xp cd does not actually fix the mbr if both drives are connected. i had to disconnect my ide drive and then fixmbr for it to actually work. maybe installing with the drive disconnected will work better.

---

### Post by Jouke74 on 2007-09-14
If you would have read the Fixmbr manual, you would have known that you have to specify /device/harddisk1 or /device/harddisk0 behind it to indiciate which drive you are installing your clean MBR to. The drive info can be obtained by typing fdisk. Actually quite a lot like Linux :) The fun is that aftwards you still need to activate the MBR to be used as boot. FIXMBR does fix the boot activation. The easiest way to do that is go to the disk management tool from windows, right click on the disk, and check make active. On each disk only one partition can be active, and this should be the one where your MBR is stored (first one, and that does not mean that it has to be the Ubuntu partition itself).

Second, why delete the partitions? You could have just as well asked the partitioner to only reformat your Ubuntu partitions.

---

### Post by YoshiHNS on 2007-09-14
I think you are mistaken. I could not actually boot into windows, nor linux, no matter what i tried. I was using the recovery option on the WinXP cd, which, as far as i know, does not require you to define which hd since you already selected where your windows installation is located, therefore working from that point. Also, my main partition was set as active.

Why delete the partitions? Just for consistency. If i was to try and do this on another computer, i would have to create the partitions. This is just to get all the steps in. Just the way i chose to do it, meaningful or not.

OK, the important info, it worked! With the IDE hd disconnected, the installation worked. First sign of the installation working was that it found information from windows that it could import. With both drives connected this never occurred. Once the installation was done, i reset the computer, grub booted up, selected the windows option, and it worked. restart, select ubuntu, and that worked. Next post will be about getting IDE drive connected.

---

### Post by praxis22 on 2007-09-15
I "dual boot" but I just switch via the BIOS, ASRock boards let you chose with the F11 key which drive to bot from, makes all the tedious mucking about scripts, etc. pointless. Though I do recommend unhooking your Linux drive while installing XP.

---

### Post by Jouke74 on 2007-09-15
> **YoshiHNS said:**
> I think you are mistaken. I could not actually boot into windows, nor linux, no matter what i tried. I was using the recovery option on the WinXP cd, which, as far as i know, does not require you to define which hd since you already selected where your windows installation is located, therefore working from that point. Also, my main partition was set as active.


Sigh.... 

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)


Fixmbr

Repairs the master boot record of the boot disk. The fixmbr command is only available when you are using the Recovery Console

fixmbr [device_name]

Parameter

device_name

The device (drive) on which you want to write a new master boot record. The name can be obtained from the output of the map command. An example of a device name is:

\Device\HardDisk0.

Example

The following example writes a new master boot record to the device specified:

fixmbr \Device\HardDisk0

Note
•	

If you do not specify a device_name, a new master boot record will be written to the boot device, which is the drive on which your primary system is loaded.
•	

If an invalid or nonstandard partition table signature is detected, you will be prompted whether you want to continue. If you are not having problems accessing your drives, you should not continue. Writing a new master boot record to your system partition could damage your partition tables and cause your partitions to become inaccessible. 


So, think again! 

Happy that it worked though :)

---

### Post by YoshiHNS on 2007-11-22
ok, i finally stopped messing around and finished this project. After Running XP and Gutsy off my SATA drive for a couple months now with no problem (aside from losing sound in Gutsy), i finished. Connected my IDE drive back up, turned the computer on expecting all sorts of errors, but no. Grub came on as usual, selected my os choice, booted no problem, at least in XP. Haven't booted Ubuntu yet.

So, instead of doing all the other editing grub and configs and whatnot, this is the easiest way to get this specific dual boot ( Linux and XP on one SATA drive, with second IDE "storage" drive).

Disconnect IDE drive
Install both OSes on main SATA drive
Reconnect IDE drive

Man that was a lot easier than i thought it would be.

PS: to jouke74. I read what you posted. The two notes at the end applied to me, which is why i did not have to define. Plus, its kind of hard to miss with only one choice. If both my drives would have been connected, then you would be right and i wrong.

PSS to jouke74. I just read through the thread again and realized the situation was as i stated a line above. Yes, you were right. With both drives i had to define which drive, which i didn't. Apologies.

Thanks for all the help all.

---

