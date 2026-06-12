---
title: "Help,could I install 64-bit?"
date: 2009-10-29
forum: x86 64-bit Users
---

### Post by lemonu on 2009-10-29
[SIZE=3]My notebook computer:
CPU:Intel core 2 P8600,@2.4GHz
RAM:2GB

Install x86 64-bit ubuntu9.10,OK?
Be able or not?[/SIZE]

---

### Post by gocek on 2009-10-29
Yeah, it should work on your notebook, because all Intel Core 2 processors are in x86-64 architecture.
You can always try running the LiveCD version, so you can make sure all of your hardwareis well supported.

---

### Post by lemonu on 2009-10-29
Thank you very much.

---

### Post by DandyDon on 2009-10-29
Should your hardware check out, AND you are currently running Windows, I would reccomend downloading EASEUS Partition Master from Snapfiles.com. It is a free disk partitioning tool that runs in 32 bit windows. You can create, remove, and resize partitions on the fly. Find it under Freeware- Disk Tools.

With Windows and Ubuntu in separate partitions, the install will be easier; and you can specify partition size to keep Windows happy. Ubuntu will automatically install the GRUB bootloader to allow you to select between Windows and Ubuntu at bootup. 

I have it dual booting XP and Hardy 64 on an Emachine with no issues.

---

### Post by lisati on 2009-10-29
I have heard anecdotal evidence that if you're going to dual-boot with Vista, then using Vista's partition manager to resize its partition is a good idea.

---

### Post by DandyDon on 2009-10-29
> **lisati said:**
> I have heard anecdotal evidence that if you're going to dual-boot with Vista, then using Vista's partition manager to resize its partition is a good idea.

I didn't know that. I know EASUS works with Vista.

---

### Post by avlinux on 2009-10-29
I'm currently running 32-bit Windows XP and would like to install Ubuntu 9.10 64-bit as a dual-boot.  Possible?  From what I read it sounds plausible but it wasn't the starting question so I just want to double check.

---

### Post by DandyDon on 2009-10-30
> **avlinux said:**
> I'm currently running 32-bit Windows XP and would like to install Ubuntu 9.10 64-bit as a dual-boot.  Possible?  From what I read it sounds plausible but it wasn't the starting question so I just want to double check.

Yes, you can.

 Download and run EASUS to set partition size under Windows. As for how big, well what apps do you want to run under Ubuntu?. Alot of apps take a lot of space, a few take a little. I have a 160 gig drive, I left 80 gigs for Windows and divided the other 80 between Ubuntu and an empty partition, which left me around 40 gigs each. NOTE: Write the gig size of the partition you wish to install Ubuntu to on a piece of paper, so you can pick the correct one during the install.

Download and create the Ubuntu 9.10 64 live CD, Use it to check hardware and driver compatibility with Ubuntu. It runs off the CD and in memory, so no changes are made to your system. 

Should you hardware and drivers check out, click Install.
NOTE: Don't install until you are sure you want to, You can play with the live CD as long as you want.

I use mine to browse the internet, and use Windows to play games. 8.04 works perfect for me, I don't know if I will upgrade to 9.10 or not.

Good Luck, and enjoy Ubuntu.

---

### Post by lemonu on 2009-10-30
Thank you,very one.
And i installed it,it works well.
Pretty good!:D

---

