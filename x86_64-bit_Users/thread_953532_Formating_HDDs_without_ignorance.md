---
title: "Formating HDDs without ignorance"
date: 2008-10-20
forum: x86 64-bit Users
---

### Post by phlembob on 2008-10-20
Hi,
I have had problems formating a SATA 500gb HDD (Seagate w/16 mg buffer).  I liked the $50 deal for 300 mg/sec transfer rate.  I remember back to the 1980s when we use to write about 5 lines format in machine language for respective HDDs.  Do we have a specific format within Debian that I can use to make a all day adventure a hour or 2 hour venture?

I did get it formated.  It was ridiculous with 24gb loss (478 gb more or less).  I used the Live CD on 3 occasions.  I checked the HDD with Windows XP x64 by formating just to see if the HDD was working.  After it accepted Windows format, I reformatted with the Ubuntu 8.04 Live CD and it took (was accepted). This consumed 13 hours all in all.  I would love some experience on this subject.  Formating was one of the prerequisites to understand computer infrastructure when the CON was green within the 13 line/screen days.  :lolflag:

Here is the a addin edit from the newly formated HDD.  It is quicker approaching scsi quickness (but not quite).

---

### Post by ajgreeny on 2008-10-20
I am not quite sure what the point of your post is.  You can format the disk using Partition Editor (gparted) in either the install of debian or ubuntu that you have or using the live ubuntu CD.  The 24 GB you "lost" is due to the 5% reserved space on an ext3 partition which is set aside to help avoid fragmentation problems amongst others. You can set a reserved size to be less than that if you want to.  I've never bothered and can't remembr how, but have a look in all the options in gparted and you may find it somewhere.

Even a 500GB disk should not take too long to format and I can't believe it would even be 2 hrs to do it.  My 250GB external disk which I changed from fat32 to ext3 took all of 5 mins from start to finish, as far as I can recall.

---

### Post by philinux on 2008-10-20
My 250's format real quick I can install a full system in about 20 mins.

Your not somehow doing a low level format?

---

### Post by dcstar on 2008-10-21
> **philinux said:**
> Your not somehow doing a low level format?

Which is totally pointless these days with the internal encoding formats of magnetic hard drives.

---

### Post by Yellow Pasque on 2008-10-21
> The 24 GB you "lost" is due to the 5% reserved space on an ext3 partition

The drive was probably 500 GiB to begin with (even though it's incorrectly sold as 500 GB) [http://en.wikipedia.org/wiki/Giga_byte#Consumer_confusion](http://en.wikipedia.org/wiki/Giga_byte#Consumer_confusion)

---

### Post by cariboo on 2008-10-21
Even windows doing a full partition and format should only take 2-3 hours. The last one I did was an 80Gb and it took about 45 minutes. How much unallocated space did windows leave on the drive, on an 80Gb it leaves about 8Gb.

Jim

---

### Post by phlembob on 2008-10-22
1st No I'm not trying to do a low-level.
2nd I was getting errors with Ubuntu and had to restart the formatting process several times.
3rd  Windows did take more than 2 hours and left less space than Ubuntu.  The ball park after the Windows NTFS was 460 gb more or less---I can't remember the exact number.

I was using the Ubuntu 8.04 Live CD and continued to get a gray box error.  That is why I used Windows to check the Seagate SATA.  I have never had a problem before with SATA-s.  After the Windows format, I used the Live CD and formated again with Ubuntu.  Why? Is what I wish to answer.  I thought that format from Terminal would be faster, but I need to learn the format construction in Ubuntu to do it properly.  If anyone knows the sizes and names of the format construction, it would be good to know.  I am checking out the format man --- inside the terminal.:guitar:

---

### Post by cariboo on 2008-10-22
Gparted is the tool to use to partition and format a hard drive the gui way. The problem with using the gui is that some features are left out, for instance you can't change the reserved block amount with a gui. If I want to work around the limitations I use fdisk to partition and mke2fs to format. There are so many options for each command that it would be best to check the man pages for each command.

Jim

---

### Post by phlembob on 2008-10-22
Thanx Cariboo
:lolflag:

PI cariboo or Alaskian Cariboo --- chuckle "caribou"

:lolflag:

---

