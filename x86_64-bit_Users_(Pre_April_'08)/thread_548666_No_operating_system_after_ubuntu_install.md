---
title: "No operating system after ubuntu install"
date: 2007-09-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by YoshiHNS on 2007-09-11
I had winXP w/SP2 installed on my HD as one whole partition. I then used the 7.04 live cd to install Ubuntu. I needed to dual boot, so i resized my main partition to make room for the linux partitions (not the manual procedure). After the install, the computer rebooted, and came up with the no operating system found. I then used the WinXP install cd, used the recovery mode to recreate the MBR. I now boot right into windows as before i installed Ubuntu. The only way i can get into Ubuntu is by booting off of the live cd and then selecting to use HD installation. What happened and how can i add Ubuntu to my os boot choices?

details
200gig maxtor sata HD
80 gig WD IDE
WinXP Pro SP2
Ubuntu 7.04 AMD64
Asus A8n5x (939)
AMD 4000+
2 x 512 corsair XMS
BFG 7950GT

---

### Post by John.Michael.Kane on 2007-09-11
These guides may help you.
[Recovering Ubuntu after installing Windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28windows%29")
[WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by dabl on 2007-09-11
> **YoshiHNS said:**
> 

details
200gig maxtor sata HD
80 gig WD IDE



A mix of IDE and SATA hard drives can be problematic for the *buntu installer, in my experience. It's particularly challenging to put Grub on a SATA drive when an IDE drive is present on the system.  Depending on which drive had Windows, and where you pointed Ubuntu to install Grub, you probably ended up with the Win XP boot record on one drive and Grub on the other.  :(

The "Alternate" Ubuntu installation CD gives you more control over where Grub gets installed.

---

### Post by YoshiHNS on 2007-09-12
ok, i tried using grub to allow the dual boot as described in the guide posted above. now i get the boot menu, but none of the entries work. Selecting Windows returns "error 12: invalid device requested",  and selecting ubuntu, normal or recovery, returns an "error 22: no such partition". I was able to get back into windows with the ubuntu live cd and boot off of hard disk, but not anymore. selecting that option just gives me a "press a key to restart". I tried to use the Win Recovery to rewrite the MBR, but that did not do anything. Any way i can remove what grub wrote in my boot record? Want to at least get back to being able to boot windows. Thinking about pulling my ide drive to i just have the sata, uninstalling ubuntu, and starting over.
working off of the live cd right now.

other thing i saw that didnt seem right. using "gksu gedit /boot/grub/menu.lst", my list was completely empty.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2        9729    78140160    f  W95 Ext'd (LBA)
/dev/hda5               2        9729    78140128+   7  HPFS/NTFS

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19948   160232278+   7  HPFS/NTFS
/dev/sda2           19949       24135    33632077+  83  Linux
/dev/sda3           24136       24321     1494045    5  Extended
/dev/sda5           24136       24321     1494013+  82  Linux swap / Solaris

---

### Post by YoshiHNS on 2007-09-12
OK, i unplugged my IDE hd and left the sata one plugged in. Turned on computer, got grub menu as before. Except now the error i get for selecting ubuntu or windows is "error 21: selected disk does not exist". I then proceeded to use the windows recovery to rewrite the MBR. It worked this time. My computer loads directly into windows now. But now i can't get into ubuntu. I tried using the live cd to boot off of first drive, but that takes me into windows. Should i try installing grubs again from here, or erase ubuntu and reinstall? Im thinking about trying grub again with the ide drive disconnected.
=------
edit
    I tried reinstalling grub as before, and it still didnt work. I was back where i was before with error 21. also, i still could not see anything in the boot/grub/menu.lst.
Im loading the menu.lst through the live cd. Im thinking i have to have the hd install of ubuntu running to actually read and edit it, whereas this empty one is the one off of the cd. i didnt mount any of the drives, just installed grub. do i need to mount the drives? Is there something obvious that i am missing?

---

### Post by John.Michael.Kane on 2007-09-12
> **YoshiHNS said:**
> OK, i unplugged my IDE hd and left the sata one plugged in. Turned on computer, got grub menu as before. Except now the error i get for selecting ubuntu or windows is "error 21: selected disk does not exist". I then proceeded to use the windows recovery to rewrite the MBR. It worked this time. My computer loads directly into windows now. But now i can't get into ubuntu. I tried using the live cd to boot off of first drive, but that takes me into windows. Should i try installing grubs again from here, or erase ubuntu and reinstall? Im thinking about trying grub again with the ide drive disconnected.

One more idea that might help.
[ dual-boot Ubuntu and windows after installing them separately on two HDs]("https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs?highlight=%28dual%29")

---

### Post by dabl on 2007-09-12
In my experience, I have got Grub to install on a SATA drive, when an IDE drive is also in the system, only with one of the following methods:

1. The IDE drive is FDISK'd, and has no format or OS on it.

2. The IDE drive is disconnected.


Method #1 is best, if you can do it, because the Linux system will "see" that drive, even though it is empty, and will recognize that it (Linux) is going on /dev/sd1 or later.  In other words, drive numbering in /etc/fstab and the /boot/grub/menu.lst will be correct.

Method #2 works, but in this case the drive numbering in /etc/fstab (and /boot/grub/menu.lst) will be "wrong" as soon as the IDE drive is re-connected, because the IDE drive will be the new "number 0" drive.  So, fstab and menu.lst must be edited, using a Live CD to boot, to add "1" to the drive numbers in fstab and menu.lst, and to make the IDE drive the new /dev/sd0 (for fstab) and hd0 (for /boot/grub/menu.lst).

Hope this helps.  :)

---

### Post by YoshiHNS on 2007-09-12
I think i found my stupid mistake. I was using root (hd0,1) instead of (sd0,1). I'm going to try that now that i know i can easily get back into windows if it doesn't work. First using method #1. If that doesn't go through, then I'll try method 2 and remap drives.

Im also thinking about uninstalling ubuntu, going back to windows as 100% of my drive, and starting the process over, using another program to repartition my hd instead of the program ubuntu uses. I found a really good thread on how to remove ubuntu somewhere, but can't find it anymore. Anyone know where it is?

---

### Post by dabl on 2007-09-12
Maybe this isn't much faster, but I think it's a little more straighforward:

1. Download the ISO and make yourself a GParted Live CD from here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

2. Partition the big drive FIRST with GParted, making the Windows partition whatever size you want it, and then make your Linux partitions as follows:

- 6GB (for "/")
- 0.5GB (for swap)
- the rest of it (for "/home")

That's a total of 4 partitions on the drive, so they can all be primary partitions, and the first one for Windows can be marked "boot".

3. Install Win XP on its partition.

4. FDISK the IDE drive and don't do anything further with it (no format).

5. Install Ubuntu, and let it put Grub where it naturally wants, which is in the MBR where Win XP is. (Use the "Alternate Install" CD and you can MAKE Grub go there, if necessary).

6. Now you can partition the IDE drive and put whatever you want there.

:guitar:

---

### Post by YoshiHNS on 2007-09-12
ok, i think i found the problem. after mounting my hd partitions and finding the ubuntu one, i went and found the menu.lst file on the hard drive. it is pointing to (hd1,0), when the only drive is (hd0). If someone could tell me how to edit the menu.lst on the hd, i think grub will work correctly. i tried sudo -e (location of file), and that directed me to some temp file. I can open the file through the explorer but it will be read only. I need to have full access to that file and make the necessary changes. i'll post fdisk and the menu.lst as on hd.

fdisk
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19948   160232278+   7  HPFS/NTFS
/dev/sda2           19949       24135    33632077+  83  Linux
/dev/sda3           24136       24321     1494045    5  Extended
/dev/sda5           24136       24321     1494013+  82  Linux swap / Solaris

media/disk-1/boot/grub/menu.list
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=3bdf5de1-9817-45e7-b413-2116faee69d2 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=3bdf5de1-9817-45e7-b413-2116faee69d2 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3bdf5de1-9817-45e7-b413-2116faee69d2 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3bdf5de1-9817-45e7-b413-2116faee69d2 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda5
title		Microsoft Windows XP Professional
root		(hd0,4)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
------------------------------
the first windows is my bartPE directory, or so i believe.
also, i tried grub> root (sd0,1), with no success. returned an error 23. Not surprised since the find /boot/grub/stage1 returned (hd0,1)
also my other 80gig IDE drive has no OS on it. i believe i formatted it as a logical partition (extended, maybe).

---

### Post by YoshiHNS on 2007-09-12
ok, i deleted ubuntu and am going to start over. i left the partitions alone, so i dont have to do any repartitioning. Going to try with both hard drives connected following the above instructions.

---

### Post by John.Michael.Kane on 2007-09-12
> **YoshiHNS said:**
> ok, i deleted ubuntu and am going to start over. i left the partitions alone, so i dont have to do any repartitioning. Going to try with both hard drives connected following the above instructions.

Please make notes of the steps you use, As it will help should you need further help.

---

### Post by YoshiHNS on 2007-09-13
made a whole thread on my second attempt to install ubuntu. here's the link

[http://ubuntuforums.org/showthread.php?t=550278](http://ubuntuforums.org/showthread.php?t=550278)

---

### Post by Tennessee on 2007-11-13
I installed Ubuntu using it's partition manager on my 2nd hard drive (D) (Vista is installed on the "C" drive.

When I removed the CD and tried to reboot I get a 'no OS found' error message. I can put the CD back in and boot to either Ubuntu or Vista from the boot menu but that is very clumsy and slow.

How do I create a boot menu that will give me these boot options without using the CD? Please don't tell me I have to wipe everything out and start over!

---

### Post by Jouke74 on 2007-11-14
First you need to make sure that the HD on which Grub is installed is the first to boot in the BIOS of your computer. 
Otherwise Windows will start straight, or no OS will be found.

Reading from your current problem, the first step, changing the boot order from the drives in the bios might even be enough....


If not: 

You need to flip HD# numbers in the grub menu (after reading the grub manual). Therefore, you need to know the names of the HD's, sda1 sda2 hda1 hda2. Which disk is which  hardware, and where are the OSes that you have installed (Xp / Vista and Ubuntu?) including for each disk the partitions you have there if there are more.

Now hd1 in linux equals Grub hd0. So you need to subtract 1 from the name of the drive. 

The partition is the second number (HD1,**#**) also starting from 0.

Use the CD to enter Linux ubuntu. Then use sudo gedit /boot/grub/menu.lst. 
Point the entries to the right locations (disks and partitions).

One catch: For Windows to work it needs to be named the first harddisk. So if windows is on HD1 then it needs to be mapped on HD0...

This is done by the following:
map (hd0) (hd1)
map (hd1) (hd0)

ak.a. for windows pretend that hd0 is hd1 and hd1 is hd0.

It's rather difficult, so please read carfully and make sure that you know what you are doing otherwise it won't help. 
If you make a typo or so, you will get the same errors if you have now... No OS found or error 17 / 21. The use the Ubuntu CD to start en alter the menu.lst again from there.

---

### Post by Tennessee on 2007-11-19
Now things are worse....I can't get Windows Vista to open at all.


I changed to boot disk in bios from HD1 back to HD2 and nothing works.  

If I click on the "Vista" boot option on the boot menu on the CD I get an error message.

---

### Post by Jouke74 on 2007-11-19
You now boot without the CD in the drive?

> If it is not working return the BIOS to the previous one. 

Which error message are you getting now?

Did you change anything in the menu.lst?

Did you read my post carefully or just went with my first suggestion only?

This way trouble shooting your problem is quite difficult...

---

