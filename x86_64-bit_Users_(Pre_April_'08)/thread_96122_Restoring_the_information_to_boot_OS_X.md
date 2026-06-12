---
title: "Restoring the information to boot OS X"
date: 2005-11-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Entity on 2005-11-28
A few weeks ago I backed up a HFS+ partition containing Panther to a disk image using dd. Since then, I've erased my entire disk and installed Breezy on it.

Last night I booted from a Dapper Drake live CD and used gparted to resized my home partition and to create an unformatted partition in order to restore the disk image to that partition using dd again.

It worked like a charm, I'm now able to mount that partition under Breezy and boot Panther using Mac On Linux. But now, I would like to make Panther available from the boot prompt on system startup. So I edited yaboot.conf and added the needed macosx=/dev/hda6 line, ran ybin but when choosing Mac OS X using the appropriate key from the prompt it keeps coming back to that same prompt.

What am I missing?

---

### Post by ssam on 2005-11-28
have you read all the documentation? there might be a trick mentioned somewhere.

what happens if you hold alt at boot time? do you get a choise of disks to boot from?

---

### Post by Entity on 2005-11-28
[QUOTE=ssam]have you read all the documentation? there might be a trick mentioned somewhere.

what happens if you hold alt at boot time? do you get a choise of disks to boot from?[/QUOTE]I tried holding ATL but, only a disk with tux appears.

---

### Post by Entity on 2005-11-28
OK my problem is solved...

I shouldn't of used gparted to create the unformatted partition as you can not specify the partition type while creating it.

The way to go is to use fdisk (mac-fdisk) and create the partition and manually specify Apple_HFS+ as the partition type (C), write the changes to partition map (w) and run ybin after the yaboot.conf modifications and you'll be finally able to boot from that partion on the system startup.

I guess the partition map has to know about the Apple_HFS+ volume.

---

