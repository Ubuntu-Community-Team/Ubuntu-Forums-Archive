---
title: "Grub Error 2 when loading Ubuntu"
date: 2008-12-26
forum: x86 64-bit Users
---

### Post by Trancegonadz on 2008-12-26
I repartitioned my hard drives yesterday and now I get a grub error 2 when ever I load. I've tried a few things but no success so far.


Info: Ubuntu 64bit 8.10 

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   476343314   238171626   83  Linux
/dev/sda2       476343315   488392064     6024375    5  Extended
/dev/sda5       476343378   488392064     6024343+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001    5  Extended
ubuntu@ubuntu:~$

---

### Post by logos34 on 2008-12-26
> **Trancegonadz said:**
> I've tried a few things but no success so far.

Did you try reinstalling grub from live cd?  (see link in my signature below)

---

### Post by Trancegonadz on 2008-12-26
I did try reloading GRUB any other ideas?

---

### Post by logos34 on 2008-12-26
Is sda set first in the Bios hard disk boot priority?  Also check your hard disk detect settings are correct--maybe they got changed somehow.  Finally try booting with sdb disconnected.

---

### Post by Trancegonadz on 2008-12-26
How do I set sda as the first in BIOS hard disk boot priority? 

I've never actually messed with my BIOS but I would presume its not set up as the first hard disk boot.

---

### Post by logos34 on 2008-12-26
Look for a 'boot' section. You should see a sub-menu in there for hard disks (as well as cd/cd, floppy/removable, etc)



You might also run filesystem check on sda1 from the live cd

sudo fsck /dev/sda1

if you repartitioned using gparted, it's supposed to automatically scan it for errors before and after, but maybe there are still some bad sectors.

---

### Post by Trancegonadz on 2008-12-26
I checked for Errors with: sudo fsck /dev/sda1 

the response was :clean

Next question: How do I disconnect sdb?

---

### Post by logos34 on 2008-12-26
Here's yet another thing to try:

When you get the error 2, press 'C' for commandline,  Then:

> 

grub> **geometry (hd0[COLOR="Red"]_[/COLOR]** press TAB at '[COLOR="Red"]**_**[/COLOR]'

(this will list partitions on boot disk.  According to fdisk, the ubuntu 6.10 / is the first partition, so it should print out type 0x83)

grub> **root (hd0,0)**   	

grub> **kernel /vmlinuz root=/dev/hd0,0**	

grub> **initrd /initrd.img**

grub> **boot**

or try (hd**1**,0)

---

### Post by Trancegonadz on 2008-12-26
I hit "C" for command line when I got the Error 2 when loading the GRUB. Nothing happened!?

---

### Post by logos34 on 2008-12-26
I wasn't sure that it would--normally you need to at least get the grub menu screen.

What exactly did you resize/repartition yesterday?

---

### Post by Trancegonadz on 2008-12-26
well... I was running Ubuntu 8.10 on sda for about 2 months. Then two weeks ago I got ahold of a Windows XP disk and I was planning to run Windows XP on the first Hard drive and Ubuntu on the second. So about a week ago I partitioned the harddrive for XP but do to the holidays never ended up getting XP loaded. A friend of mine gave me an old laptop so I'm going to be using that for XP. Since all this happened I decided to load Ubuntu on both Sda and sdb. This ment that I partitioned both sda and sdb to run for ubuntu. When I tryed to load Ubuntu again I now get Grub error 2

---

### Post by logos34 on 2008-12-26
*think *I understand now...so yeah just disconnec the power plug on sdb and see if you can boot..we;ll go from there

---

### Post by Trancegonadz on 2008-12-26
If there is a tutorial on how to wipe everything clean and start over I'm more then open to try that if nothing will work!!!

I clearly don't know enough about computers!

---

### Post by logos34 on 2008-12-26
hopefully you can boot it without sdb connected...then all you'll have to do is boot the live cd and use gparted to wipe sdb completely

---

### Post by Trancegonadz on 2008-12-26
Unplugging sdb worked! 

Now I guess the question is how do I get the computer to recognize the other Array?

---

### Post by logos34 on 2008-12-26
what do you mean 'array'?  did you try to configure this as RAID?  EVMS?

If you can now boot back into ubuntu, then you want to power off, reconnect sdb, reboot the live cd, open system>admin>partition editor and delete the extended partition sdb1.  Then reboot to the hard disk again.

---

### Post by Trancegonadz on 2008-12-26
umm... alright I'll give it a shot!

---

### Post by Trancegonadz on 2008-12-26
I still get GRUB error 2 even though I did what you told me too!

---

### Post by caljohnsmith on 2008-12-26
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. Also, for whichever is your linux partition (sda1?), please post:
```
sudo dumpe2fs /dev/[COLOR="Blue"]sda1[/COLOR] | grep -i "inode size"
```
But change sda1 above if linux is actually on a different partition.

---

### Post by logos34 on 2008-12-26
> **Trancegonadz said:**
> Since all this happened I decided to load Ubuntu on both Sda and sdb. This ment that I partitioned both sda and sdb to run for ubuntu. When I tryed to load Ubuntu again I now get Grub error 2

You're going to have to explain exactly what you meant by this...If you actually tried to install a second instance of ubuntu on sdb rather than just make it storage, then grub may also be on the MBR of that drive.  Not sure how far you got because all I saw was an extended partition.  

> **Trancegonadz said:**
> Unplugging sdb worked!

Great.  At least you can boot without it.

> **Trancegonadz said:**
> I still get GRUB error 2 even though I did what you told me too!

Sounds like what may be happening is the machine keeps making sdb (IDE or Sata?) the boot drive as soon as you connect it...Check the Bios...Grub may be on the MBR...You can remove it with the 'Uninstall' option on the Super Grub Disk (see link in my signature) or by simply doing 

**sudo dd if=/dev/zero of=/dev/sdb bs=446 count=1**

---

