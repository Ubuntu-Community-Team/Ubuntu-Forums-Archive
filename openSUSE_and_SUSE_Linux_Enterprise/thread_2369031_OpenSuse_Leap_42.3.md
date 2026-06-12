---
title: "OpenSuse Leap 42.3"
date: 2017-08-17
forum: openSUSE and SUSE Linux Enterprise
---

### Post by archp2009 on 2017-08-17
I have a multiboot system including many linux partitions and Windows partitions booting from Grub2. I have been a week or two not being able to figure out what to do to install OpenSuse Leap 42.3 in a partition that used to contain OpenSuse 13.2 even though I have been geting help from the Opensuse forums.   Is it enough to reformat that partition before installing the new OpenSuse distro or is it essential to delete the partition.  The problem is that the expert partitioner sees the reformatted partition as being already mounted so Expert Partitioner does not give me the option of a single slash / mount point. I seem to recall that I needed to be walked through Opensuse 13.2 a coupld of years ago, so I probably need someone to walk me through this one. I find Ubuntu very simple to install but not Opensuse.  Thanks for your kind consideration.

---

### Post by oldfred on 2017-08-17
I know nothing about OpenSuse, but does it now use LVM which is an advanced partition scheme?
[https://doc.opensuse.org/documentation/leap/reference/html/book.opensuse.reference/cha.advdisk.html](https://doc.opensuse.org/documentation/leap/reference/html/book.opensuse.reference/cha.advdisk.html)
It may now also default to btrfs where Ubuntu defaults to ext4. I also no nothing about btrfs.

You then have to use LVM tools.
I know some that have installed other versions that default to use LVM to just use the standard ext4 partitions like Ubuntu. One of advantages of LVM is when it manages entire hard drive, but if only part of drive it is a disadvantage as some partitions can be edited with gparted and others only with LVM tools. And you have to install LVM drivers in all installs.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

Post this:
sudo parted -l

---

