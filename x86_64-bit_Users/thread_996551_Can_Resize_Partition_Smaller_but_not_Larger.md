---
title: "Can Resize Partition Smaller but not Larger"
date: 2008-11-28
forum: x86 64-bit Users
---

### Post by bruc33ef on 2008-11-28
I have a Vista-Ubuntu (Intrepid) 64bit dual-boot system (Lenovo 3000 N200) on a 160gb hard drive with only 20gb partition for Ubuntu.  Now I want to expand the Ubuntu partition.  BUT, GParted (running from a LiveCD will only let me reduce the partition size.  Yes I have tried to reduce the Vista partition first but it still won't let me expand the Ubuntu partition.  I have also tried formatting some free space to ext3 first, but that doesn't work either.

Many thanks to anyone who can tell me what's going on.

bf

---

### Post by nikgare on 2008-11-29
> Yes I have tried to reduce the Vista partition first

Did it work?
Where is the space that's left over?

---

### Post by bruc33ef on 2008-11-29
> **nikgare said:**
> Did it work?
Where is the space that's left over?

Nah, it didn't work.  The leftover space can be set up as a new partition (in the space taken from the Vista partition) but not part of the Ubuntu partition.  I tried formatting it to ext.3 but that doesn't do it either.  I end up with a Vista partition, a Ubuntu partition and an extra ext.3 partition.

I wonder whether it has something to do with the fact that I use the 32-bit Vista on the same drive as the 64-bit Intrepid.

---

