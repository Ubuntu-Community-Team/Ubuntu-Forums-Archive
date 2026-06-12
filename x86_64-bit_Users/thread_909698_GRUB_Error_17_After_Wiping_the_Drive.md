---
title: "GRUB Error 17 After Wiping the Drive"
date: 2008-09-03
forum: x86 64-bit Users
---

### Post by heyjim on 2008-09-03
I'll try to give as much background info as possible.

I have a laptop hp dv9500t with TWO harddrives.

I have windows vista ultimate installed on my primary (want to downgrade to XP)

Ubuntu installed on secondary drive

I use GRUB to select between the two OSes

Recently I have used an Ultimate Boot CD to wipe my second drive as I want to make it storage only for my window's vista comp.

After wiping, GRUB boots up and gets an error 17 message.

How do I remove GRUB and get back my 2nd storage space.

I have tried DOS command fdisk /mbr etc with no succes...

Any help is appreciated.

thanks for your time

heyjim

---

### Post by caljohnsmith on 2008-09-03
So you wiped the Ubuntu HDD clean, true? In that case you want to replace the Grub master boot record (MBR) on your Vista HDD back to a Windows MBR, so you can boot Windows, correct? If that's true, then there are many ways to fix that problem. If you have a Vista Recovery CD/DVD, just boot it up, enter the recovery console/command line, and run the command:
```
bootrec /fixmbr
```
Or if you have Windows XP install CD, boot it up, go to the recovery console, and run:
```
fixmbr
```
Note that the Windows XP MBR can boot Windows Vista and vice versa. If you don't have either a Vista CD or Win XP CD, there are other ways to do it too. Let me know how it goes or if you need further info on alternate methods.

---

### Post by Kilz on 2008-09-03
Have fun in virus land :)

---

### Post by heyjim on 2008-09-04
> **caljohnsmith said:**
> So you wiped the Ubuntu HDD clean, true? In that case you want to replace the Grub master boot record (MBR) on your Vista HDD back to a Windows MBR, so you can boot Windows, correct? If that's true, then there are many ways to fix that problem. If you have a Vista Recovery CD/DVD, just boot it up, enter the recovery console/command line, and run the command:
```
bootrec /fixmbr
```
Or if you have Windows XP install CD, boot it up, go to the recovery console, and run:
```
fixmbr
```
Note that the Windows XP MBR can boot Windows Vista and vice versa. If you don't have either a Vista CD or Win XP CD, there are other ways to do it too. Let me know how it goes or if you need further info on alternate methods.

Thanks, I ended up just getting an XP CD and using a guide I found to completely wipe and downgrade to XP

> Have fun in virus land :)

Err....Thanks, I have ESET NOD32 SS so I should be fairly fine for a while.

---

### Post by svt8uup on 2008-09-09
> **heyjim said:**
> I'll try to give as much background info as possible.

I have a laptop hp dv9500t with TWO harddrives.

I have windows vista ultimate installed on my primary (want to downgrade to XP)

Ubuntu installed on secondary drive

I use GRUB to select between the two OSes

Recently I have used an Ultimate Boot CD to wipe my second drive as I want to make it storage only for my window's vista comp.

After wiping, GRUB boots up and gets an error 17 message.

How do I remove GRUB and get back my 2nd storage space.

I have tried DOS command fdisk /mbr etc with no succes...

Any help is appreciated.

thanks for your time

heyjim




I'm just a new kid on the block, but have had the same error message. I found my fix at [http://mirror.href.com/thestarman/asm/mbr/BootToolsRefs.htm#PQMBR](http://mirror.href.com/thestarman/asm/mbr/BootToolsRefs.htm#PQMBR)
 It's small programs to copy mbr from and to hdd. there is also instructions and command examples, short of a few santax's not included, I copied from an identical drive and saved alot of time.

---

