---
title: "Installed a Second IDE Hard Drive On My Apple G3"
date: 2005-12-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by gconn77 on 2005-12-18
I see that the system recognizes it... however, how can I start using it?

---

### Post by gruepig on 2005-12-18
Conceptually, there are three separate steps to using your hard drive once it is recognized as a device.  First, you need to partition it.  Then, you need to initialize your partition(s).  And finally, you can mount the partition(s).

In gnome, go to System -> Administration -> Disks.  Select your device and go to the partitions tab.  If you see free space, create partitions as needed.  Then form the filesystem (e.g., ext3 or Extended 3), and specify an access point (mount path, e.g., /mnt).

Or from the command line:

Partition your hard drive:
mac-fdisk (or fdisk, cfdisk)

Initialize a partition as ext3:
sudo mke2fs -j <your_partition>

Mount the partition at /mnt:
mount -t ext3 <your_partition> /mnt

Check that your partition has mounted (any of the following):
cat /proc/mounts
mount
df
ls /mnt

Unmount the partition (make sure you're not using it, e.g., 'cd /':
umount <your_partition>

To mount automatically on boot at /mnt:
Add the following line to /etc/fstab:
<your_partition> /mnt ext3 defaults,errors=remount-ro 0 2

where "your_partition" is the device name of your partition, something like /dev/hda2, /dev/sda3.

(Note that if you have any data already on the hard drive, formatting and initializing will erase it.)

---

