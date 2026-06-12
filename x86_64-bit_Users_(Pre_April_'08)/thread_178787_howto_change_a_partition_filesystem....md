---
title: "howto change a partition filesystem..."
date: 2006-05-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by Anguilla on 2006-05-18
I have a lacie 250gb external hard drive, the problem is that I have parted it in 4 Fat32 partition, now with osx is impossible to change the filesystem of only one partition to hfs+ without erasing the whole disk and making everything from a brandnew partion table...

so, is it possible with a ubuntu live cd?
can I write a new hfs+ filesystem on a partition of my disk?

thanks, Anguilla...

---

### Post by infoburner on 2006-05-18
you can do that with gparted.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

go to download and download the cd image, its a live cd.

it gives you a graphical look at the partitions on your disk. just delete the old partition and leave it as unused space for osx to format, or you can create a new partition and format it as hfs. gparted can resize hfs+, but it cant create new hfs+ partitions, only hfs

good luck!

---

### Post by Anguilla on 2006-05-18
yes but is only for x86 and not for PPC... does ubuntu live includes gParted???
so I can try with ubuntu live...

---

### Post by ssam on 2006-05-18
ubuntu has gparted, and it is on the live cd. its not the hottest new version, but i am pretty sure it will let you change a fat partiton to hfsplus.

you could try the [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) powerpc live cd, if you need a new version gparted. but i have not used it so can't comment on how stable it is. usually changing partition types is a lot safer than things like resizing and moving partitions.

---

### Post by Anguilla on 2006-05-18
I'm using gParted, but I'm having some problems, I have 2 primary partition fat32, 90gb each one, I deleted the other two logical partitions, I had to make an estended one in the free space, but the problem is that if I try to use the HFS filesystem, Gparted only let me use max 2gb for the new partition, why?????

---

### Post by Anguilla on 2006-05-18
I thinks it doesn't support hfs+ but only hfs....

---

### Post by seatea on 2006-05-18
i have been messing with an Iomega external hard drive for a couple of days. I haven't yet got it formatted right with the partitions I wart. I don't have Mac OS X and the drive setup utility of Mac OS 9 won't partition the drive. I found  a way with a product called el gato to make my partitions, but the Breezy installer won't recognize them which makes it  impossible to set up the drive as a multiboot system.  After looking around, I have found a utility in ubuntu called mac-fdisk. I haven't used it yet because there is a steeper learning  curve for using it than I am ready for at the present. You might be able to use it to make the HFS filesystem on your drive. It is not a gui based utility. Look at man mac-fdisk.

I looked  at the  man pages again for mac-fdisk. It  doesn't say whether or not it can create hfs+ filesystem. It may not help then. Sorry.

---

### Post by Anguilla on 2006-05-18
I tried mac-fdisk, but I found some problems:

If I "print" the partition table in parted I get the list of sda1,sda2,sda3 all with their own decription, but if I try to print the same partion table with "mac-fdisk" it says that no partion table exist on the disk, so I'm thinking that it not possible to write a hfs filesystem without a new partion table made by mac-fdisk, but if I do like this I'm gonna lose all my files... isn't it?

---

### Post by Ptero-4 on 2006-05-18
If you write a new partition table you lose your partitions b/c the new table won't recognize the layout of the old one since each one is designed differently.

---

