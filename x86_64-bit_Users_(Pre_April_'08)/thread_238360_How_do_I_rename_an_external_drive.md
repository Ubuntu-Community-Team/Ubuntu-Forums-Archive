---
title: "How do I rename an external drive?"
date: 2006-08-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by cocteau on 2006-08-17
Hi

I have a usb hd that I would like to show up as something different than usbdisk on the desktop when I plug it in. Is there a way to rename the drive to something different, like maybe lunch?

kenneth

---

### Post by givré on 2006-08-17
Is it an ntfs or an fat32 one.
For ntfs, you will have to use ntfslabel in the ntfsprogs package.
For fat32, i don't really know.

---

### Post by waldschm on 2006-08-17
This should help
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by givré on 2006-08-17
wha great link, thanks :D 
The wiki is definitly my friend 8-)

---

### Post by cocteau on 2006-08-20
Thanks.

It was an ext3 drive. And it's much better now :)

---

### Post by browneyedgirl65 on 2006-09-11
How do you figure out what sort of partition (fat32, ntfs or ext3)?  The instructions for renaming any of these types are excellent, but I'm not sure what I've got on my external drives...!

---

### Post by cocteau on 2006-09-12
> **browneyedgirl65 said:**
> How do you figure out what sort of partition (fat32, ntfs or ext3)?  The instructions for renaming any of these types are excellent, but I'm not sure what I've got on my external drives...!

As far as I remember the command is

fdisk -l

in a terminal, which will give you detailed information about all harddrives. I'm not 100% sure about the switch though, so I may be wrong. Anyway, it's the fdisk command for sure.

---

