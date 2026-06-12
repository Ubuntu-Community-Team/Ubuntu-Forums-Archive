---
title: "Getting Ubuntu installed"
date: 2005-12-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by miracle` on 2005-12-12
Hey,

so here's the deal, I've been bussy with Fedora but it has been months since my last look at it and since we are all using Ubuntu at university i'm kinda obliged to switch up to Ubuntu. Since i've got a AMD64 processor i've downloaded en burned my AMD64.iso to disc and ran the setup. So far so good, i had 30GB of left space on my hf so used 25GB and created a fat32 partition on which i was willing to continu the install and a 2.5GB swap partition. Left 2.5 of free space because I don't know if windows is using a swap included in the used space of it on de Ubuntu setupdisplay. The setup started and aborted on like 20% of the installation saying it couldn't save the bootstrap somehow :s

I'm using a SATA Maxtor HD if this can be of any help. Any help would be greatful! thx! BTW, the community is gorgious!

---

### Post by RAOF on 2005-12-12
You can't install Ubuntu onto a fat32 partition.  It just doesn't have the needed features (no file privileges, no symlinks, no hardlinks).  You'll need to create a partition with a file system that works (ext3, reiserfs, whatever.  Just not fat32) and install Ubuntu on there.  You can still leave most of the fat32 partition for sharing information between windows & linux, but linux **must** be installed on a more modern filesystem.

---

### Post by miracle` on 2005-12-14
Thx for your reply! Installed Ubuntu and i'm now trying to get my Wireless pci card functional. I've been trying to search for the firmware on the US Robotics site but can't seem to find it... I'm using a U.S. Robotics 802.11g Wireless Turbo Adapter Model USR805416. If anyone could hook me up with some extra info on this one ?

---

