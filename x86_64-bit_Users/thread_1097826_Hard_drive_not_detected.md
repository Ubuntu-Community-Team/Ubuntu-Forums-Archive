---
title: "Hard drive not detected"
date: 2009-03-16
forum: x86 64-bit Users
---

### Post by JimmyA on 2009-03-16
I have a Fujitsu Siemens AMILO Pa 2510.
I recently installed Kubuntu on it after testing Ubuntu.

My computer has 2 harddrives, but Kubuntu can only detect one of them, however Ubuntu detected both of them.

Why won't Kubuntu detect the other hard drive?

Thank you for helping:)

---

### Post by JimmyA on 2009-03-18
Can anyone help me?

---

### Post by Drellir on 2009-03-18
I must warn you but I'm I total newbie but I stumbled into a similar problem. I have a Windows boot up also on my computer. So to put it short my Kubuntu froze one day (think it had something to do with my Amrok but after that incident. I did not have any access to my two hard drives. So I found it somewhere that I had to open windows close it properly and then I could access my hard drive.
Hope it will help.

Drellir
:P

---

### Post by philinux on 2009-03-18
> **JimmyA said:**
> I have a Fujitsu Siemens AMILO Pa 2510.
I recently installed Kubuntu on it after testing Ubuntu.

My computer has 2 harddrives, but Kubuntu can only detect one of them, however Ubuntu detected both of them.

Why won't Kubuntu detect the other hard drive?

Thank you for helping:)

Post the output of this

```
sudo fdisk -l
```

---

### Post by Yellow Pasque on 2009-03-18
If fdisk doesn't show two drives, make sure the drive is showing in the BIOS. If it doesn't show in the BIOS... I hope you had the data on it backed up. :(

---

### Post by JimmyA on 2009-03-20
> **Drellir said:**
> I must warn you but I'm I total newbie but I stumbled into a similar problem. I have a Windows boot up also on my computer. So to put it short my Kubuntu froze one day (think it had something to do with my Amrok but after that incident. I did not have any access to my two hard drives. So I found it somewhere that I had to open windows close it properly and then I could access my hard drive.
Hope it will help.

Drellir
:P

I have only Kubuntu as I made a clean install on the main hard drive.

> **philinux said:**
> Post the output of this

```
sudo fdisk -l
```

> **Temüjin said:**
> If fdisk doesn't show two drives, make sure the drive is showing in the BIOS. If it doesn't show in the BIOS... I hope you had the data on it backed up. :(
The output is translated from Swedish(Hope I got it right;))
```

Disc /dev/sda: 250,0 GB, 250059350016 byte
255 heads, 63 sectors 30401 cylinders
Drives = cylinders of 16065 · 512 = 8225280 byte
Discindentifier: 0x734c0879

    Drive Start   Beginning      End       Block    Id  System
/dev/sda1   *           1       29699   238557186   83  Linux
/dev/sda2           29700       30401     5638815    5  Extended
/dev/sda5           29700       30401     5638783+  82  Linux Rotation / Solaris

```

---

### Post by Yellow Pasque on 2009-03-20
fdisk only shows one drive. Can you check in the BIOS to see if the missing drive shows there?

---

### Post by JimmyA on 2009-03-20
It doesn't appear in BOIS either.

It seems like the drive is 250 GB. That's the same size my 2 drives were in Windows(one was 180 GB and the other 70 GB :S).
BIOS also says that my drive is 250GB.

---

### Post by Yellow Pasque on 2009-03-20
That's strange. It almost sounds like the PATA/SATA mode setting in your BIOS got switched to "RAID" somewhere along the way..

---

### Post by JimmyA on 2009-03-20
When checking BIOS I can see that the disc in connected to SATA port 1, if that helps.

---

