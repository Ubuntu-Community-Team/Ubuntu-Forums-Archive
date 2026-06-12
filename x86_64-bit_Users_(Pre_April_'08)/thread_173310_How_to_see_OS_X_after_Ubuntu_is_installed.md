---
title: "How to see OS X after Ubuntu is installed?"
date: 2006-05-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by camgangrel on 2006-05-10
Ok I have looked for this and have not found anything this far. What I have is a Wallstreet 233 Mhz G3 with 160 MB of RAM and I have OS 9.2.2 on one part of this hard drive as to boot both OS X 10.4.6 and Ubuntu. Anyway what I want to know is there a way to make my OS X part of the hard drive show up so I can use files off it. Right now if I want to get a file I have to boot into OS X then copy my files over to my G4 Power Mac over the network then reboot into Linux then log into my G4 and copy over the files. My copy of Ubuntu is the one that is comeing on the CDs that are shiping. something like 5.10 or some like that. Now 2nd thing is I have install Ubuntu on my Power Mac G4 450 Mhz x 2, 1.5 GB of RAM two 40 GB hard drives. Anyway how do you add OS X into the boot loader? Because when I restart I have to hold down my option key to be able to boot into OS X. When I have just rebooted it had no place for my OS X to be booted. All it has is just Linux listed? And how do you go about after adding OS X to the Boot loader to make OS X, the OS that it boots to with out anyone to do anything to it? Thank you all ahead of time, for all your help and time.

---

### Post by dynamicv on 2006-05-10
Ubuntu already supports the HFS+ file system used by Mac OSX.  You need to create a mount point in your Linux Terminal to mount the OSX partition.

mkdir /mnt/macosx
mount /dev/**hda#** /mnt/macosx -t hfsplus

To get the **hda#**, run the "fdisk -l" command (that's a lower case L).  The large hfs+ partition is the most likely one you want.

If this works, you can get the system to mount the partition automatically at bootup by amending your /etc/fstab file.

EDIT:  As for your other problem, the solution posted over on the Yellow Dog site will work if you amend it accordingly.

[http://www.terrasoftsolutions.com/support/solutions/ydl_general/yaboot_osx.shtml](http://www.terrasoftsolutions.com/support/solutions/ydl_general/yaboot_osx.shtml)

---

### Post by camgangrel on 2006-05-10
Thank you.

---

