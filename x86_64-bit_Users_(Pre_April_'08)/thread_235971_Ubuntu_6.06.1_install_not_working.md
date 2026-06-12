---
title: "Ubuntu 6.06.1 install not working?"
date: 2006-08-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by dre2004 on 2006-08-14
Hi,

I've tried installing 6.06.1 on my AMD 64 but seem to having issues. 

To give a bit of background here is what I have

AMD 64 dual core 4400
2GB ram
4 x 300 GB SATA drives
Nvidia 7800 GTX

Ok so last night I tried several times to install ubuntu to /dev/sdb without any luck.

I thought initially it could be because I created a 15 GB root parition and possibly where the kernel had been written grub couldnt access, but that wasnt the case.

The paritioning scheme I used is as follows
/boot 4GB (sdb1)
/     15GB (sdb2)
swap  4GB (sdb3)
/usr  20GB (sdb5)
/var  20GB (sdb6)
/home The rest of the space (sdb7)

So the install appears to complete correctly and asks to reboot which I do BUT it seems grub has issues. I've had a couple of different errors (error 15, and error 18 I think)

I've tried booting from the install cd again and chrooting to where I've actually installed ubuntu to and running grub-install /dev/sdb manually which looks ok but still no luck.

I'm not too sure what the installer is doing in terms of if its installing it to the MBR of /dev/sdb or if its putting the bootloader in the beginning of /dev/sdb2. 

Is there some other means of installing which gives more detail as to what is going on? Or possibly a log file I can check?

---

### Post by dre2004 on 2006-08-15
Anyone have any ideas? I looked through the boot options of the install CD and there is meant to be a live-expert which doesnt seem to work. :confused: :confused: :confused:

---

### Post by dre2004 on 2006-08-16
Still no luck I am going to try updating grub or possibly installing it from source to see if that helps any.

From what I can tell the install has worked fine (just because there is no errors) but not too sure what happens in terms of grub. I cant find a log file which tells me anything so I'm going to assume its ok.

---

### Post by hajk on 2006-08-16
You're not getting much response here, dre2004, what with a setup with 4 big SATA disks... Could that be the problem? Master/slave settings? BIOS settings? You would expect that even the version of GRUB in the Dapper repositories is quite capable, and often used on servers with multiple drives -- not much sense in trying the latest version without checking some of the more likely solutions first.

---

### Post by dre2004 on 2006-08-16
I'm not sure if the 4 SATA disks is the problem or not, I've got two other distro's installed and they're working without a problem.

I have checked the BIOS settings and they appear to be fine, what I find odd is that on the drive I'm trying to install ubuntu to I did previously have Fedora Core 3 running on. 

I might try disconnecting the other drives and doing the install that way to see if it helps any.

---

### Post by dre2004 on 2006-08-17
I found what the issue was it was the Ubuntu 6.06.1, I tried installing Ubuntu 6.06 and it worked like a charm.

---

