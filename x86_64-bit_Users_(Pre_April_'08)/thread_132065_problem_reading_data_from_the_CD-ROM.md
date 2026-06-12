---
title: "problem reading data from the CD-ROM"
date: 2006-02-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by vipatus on 2006-02-17
Please help me I'm despred  .

I have a AMD64 PC and I'm trying to install kubuntu-5.10-64-bit. I have checked image by md5sum and it's okey. 

Boot starts well.. Choosing language, keyboard, detecting and mounting CD-ROM, Scanning CD-ROM goes well but after that when it's trying to load installer components from CD it stucks.
 It says that there was a problem reading data from the CD-ROM, please make sure it is in the drive??? 

Is there something wrong with my DVD player or what? 

I don't know what to do. please help me..

---

### Post by majik279 on 2006-02-19
Have you booted from this drive before? How old is the drive?

---

### Post by vipatus on 2006-02-19
Hi,

Yes I have. I have installed XP and it went well.
Drive is brand-new, whole computer is new one.

I appreciate your help O:)

---

### Post by Herring on 2006-02-21
This sounds exactly the same as my problem: [http://ubuntuforums.org/showthread.php?t=128809](http://ubuntuforums.org/showthread.php?t=128809)
(which I still haven't solved).

The fact that it does it with different disks on different media but always at the same point in the install implies that it's loading something which is stopping the CD/DVD from working. If only I could find out what.

---

### Post by Daggett on 2006-02-21
Is your CD/DVD drive an SATA drive?   If so, that's probably the issue.  I'm not sure about Kubuntu, but you can't install Debian AMD64 from an SATA CD/DVD drive.  The kernel sets a parameter called atapi_enabled to 0 by default. It has to be set to 1 for the installer to recognize the drive.  I can't find a way to set it to 1 from the linux boot prompt.  The line "libata.atapi_enabled=1" is supposed to work, but it doesn't.

---

### Post by bigmo on 2006-04-03
Try Flight6..
UI had the same problem and tried everything I could to no avail..
Flight6 live CD works.. I have also noticed the is an option in it to check the CD...
That could only mean Ubuntu aware of the issue...

---

