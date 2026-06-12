---
title: "Kubuntu 7.10 DVD Partitioner won't"
date: 2007-11-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by hangfire on 2007-11-16
I am trying to install from Kubuntu 7.10 64bit DVD on my trusty 3400+/754 ($99 Biostar newegg special). It has an IDE WD600 (6.06LTS) as /dev/hda (that I want to leave untouched) and I'm installing to /dev/sda, which is a new Samsung SATA 500GB drive.

The problem is... I have already partitioned on the 500G a /dev/sda1 (/boot), /dev/sda2 (/), and /dev/sda3 (/home), and I want to put SWAP on /dev/sda5 after the Extended partition of /dev/sda4. Then make a filler partition for the rest of the disk, like /space on /dev/sda6. Simple, right? Ha!

Well, going into the manual partitioning s/w, if I create an EXT3 for the next partition after /dev/sda3, it helpfully makes it /dev/sda5, I suppose it is helpfully helping me by secretly creating the Extended partition of /dev/sda4. But that's not the layout I want.

The problem is, when I try to put swap as /dev/sda5, it doesn't allow me to manually create the Extended sda4, it puts SWAP in as Primary /dev/sda4 that's the max number of primary parts for an MSDOS label drive, and then I can't use the last 300G of disk left free. Ha!

Can someone tell me how to make this program... less helpful? Or, if I just bypass it and finish partitioning the disk using fdisk from the shell, how to I get the installer to know which partitions to install to and where to mount them, in particular to leave /dev/hda entirely alone and to NOT FORMAT /dev/sda3 (/home) which is already populated?

Is this just a glaring bug in the partition s/w, does it only happen with /dev/hda exists as well?

Sorry, folks, but this is as bad as Red Hat's partitioners moving partitions around on me as I enter them. I always bypass it as well.

-HF

---

### Post by hangfire on 2007-11-16
After thinking about it for a minute, I partitioned /dev/sda correctly with **sudo fdisk /dev/sda** , then went back to the keyboard langauge selection and then back to the partitioner (ubiquity?). It wouldn't let me format /dev/sda6, the checkbox refused to select no matter how many times I clicked on it, so I formatted it manually from the command line myself. I could get the format checkbox selected on all the other partitions (except /home of course).

It's installing now (off to bed).

So, just what is the name of the partitioner, so I can enter a bug report on it?

-HF

---

### Post by hangfire on 2007-12-11
Bump

---

### Post by Jouke74 on 2007-12-12
I think it's called Gparted.

---

### Post by rsw686 on 2007-12-12
The extended sda4 partition contains the sda5+ partitions. You might look at using LVM as it dosn't have any limitations. You create two partitions /boot and the LVM. With the LVM manager you create a volume group and then logical volumes (like a partition) for each mount point you like. In the future you can easily resize them if needed.

---

### Post by hangfire on 2007-12-19
> **Jouke74 said:**
> I think it's called Gparted.

Thanks. Most graphical partition editors call gparted. However I know for a fact that gparted does not have this limitation. It is the GUI front-end that imposes it.

-HF

---

### Post by hangfire on 2007-12-19
> **rsw686 said:**
> The extended sda4 partition contains the sda5+ partitions. You might look at using LVM as it dosn't have any limitations. You create two partitions /boot and the LVM. With the LVM manager you create a volume group and then logical volumes (like a partition) for each mount point you like. In the future you can easily resize them if needed.

Thanks, but they'll be tossing handpacked frozen spherical projectiles in torrid subterranean regions before I go back to LVM. Been there, lost that data, got the T-Shirt.

-HF

---

### Post by rsw686 on 2007-12-19
> **hangfire said:**
> Thanks, but they'll be tossing handpacked frozen spherical projectiles in torrid subterranean regions before I go back to LVM. Been there, lost that data, got the T-Shirt.

-HF

Never had an issue. I use LVM all the time. You really need to read all the directions and things about before you rely on it.

---

