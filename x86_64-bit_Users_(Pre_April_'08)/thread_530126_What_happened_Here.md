---
title: "What happened Here?"
date: 2007-08-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by gaylapdancer on 2007-08-20
OK guys.

I expanded my ~160gb EXT3 partition to ~300gb using GParted Live cd. This took ~16 hours as The partition was moved to the front of the drive before being expanded.

This operation completed successfully and Ubuntu boots. I entered 
```
df -k
```
To get a disk usage percentage and It said I had used 98%.

This is quite a concern as I only had ~50gb of stuff on the partition in the first place.

I opened GNOME partition editor to check the partitions, and the partition is ~300gb which it should be.

I discovered most of my files had been duplicated, in my Music file's case, 12 times. I cleared the duplicates, and the usage dropped down to what it was before the partition change.

I then opened Disk Usage Analyzer, and It told me that my partition was only 136.8gb, About what it was originally.

Why would Ubuntu not recognize that it now has a large amount of space? It doesn't seem to realize that the partition has changed size, Is there an additional step?

Any help is -GREATLY- appreciated

---

### Post by PacketCollision on 2007-08-20
It seems like parted did quite a number on your drive.  Run "sudo fsck -f /dev/*sda1*" (where *sda1* is the name of your partition), then run "sudo cfdisk /dev/*sda*" (where *sda* is the name of your drive).  Check to see if the size is correct.  If it is, you're in luck, run "sudo resize2fs -p /dev/*sda1*" to make sure the filesystem is the correct size.

If the partition is not listed as being the right size in cfdisk, but the partition *has* been moved to the correct space, you can delete and recreate the partition to use the extra space.  This won't damage the partition as long as the starting place is the same.


Note: every one of the commands I've mentioned could hose your system, please back up, and don't blame me if your computer explodes.

---

