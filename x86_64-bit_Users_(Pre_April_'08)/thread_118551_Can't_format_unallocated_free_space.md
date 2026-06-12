---
title: "Can't format unallocated free space"
date: 2006-01-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by txcrittr on 2006-01-17
I have an Abit KV8 Max3 motherboard with an Athlon 64 3200+ processor. Hard drive is a 114GB Maxtor. My graphics card is an ATI Radeon 9800 Pro agp.

I have Win2k and Ubuntu installed already. I used Knoppix to shrink my Win2k NTFS partition so I could get Ubuntu installed.

QtParted currently reports

01    /dev/hda1    ntfs    Active     35.52GB
02    /dev/hda3    ext3                    4.66GB
03    /dev/hda-1   free                   43.06GB
04    /dev/hda4    extended        964.84MB
05    /dev/hda5     linux-swap       956.99MB <This is a subset of hda4>
06    /dev/hda6    fat32                  29.78GB

When I use Knoppix to run Qtparted, the first thing I must do is # swapoff /dev/hda5 to stop Knoppix from using the swap partition.

After that I can delete, format, move or perform some function to all partitions except /dev/hda-1. I can only get properties.

Just on a lark I went into my win2k to try to format that partition and it aint happening there either.

Any suggestions on how to get this 40 some odd gigs back in service without losing win2k or Ubuntu?

---

### Post by Azion on 2006-01-17
Do a disk check on it.
Just to see if it could be bad blocks, or the tables for your HD.
Try defragging it on 2k too

---

### Post by RAOF on 2006-01-17
I'd be rather alarmed by the device name - "/dev/hda-1".  Never seen that type of numbering before.  It's especially weird since you *also* have a "/dev/hda1".  Maybe there's something messed up in your partition tables?

---

### Post by VSFH on 2006-04-15
My suggestion to you would be to back up all of your data and completely erase the entire drive. Format it with qparted (is fdisk still used at all?) or your partition program of choice - but I wouldn't use XP's. Install XP, then install Ubuntu over again; if your partition tables are crossing (I use fdisk primarily, so don't know if you can see different logical / physical endings of drives in qparted) and you continue writing data to the partition, you may physically damage your drive. My suggestion, again, would be to back up your data and scratch the whole bit.

---

