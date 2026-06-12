---
title: "[SOLVED] Hardy disk mapping changes?"
date: 2008-10-04
forum: x86 64-bit Users
---

### Post by ddales on 2008-10-04
Hi all, I believe I have officially landed in Bizarro World!  Somehow, my disk mappings occasionally change on reboot.  I'm a pretty experienced Linux user and don't understand this at all.  

For example, my boot drive was originally /dev/sda.  But sometimes, after rebooting, the device labels change and my boot drive suddenly becomes /dev/sde which belongs to my Raid device.  WTF!?

This is a major problem because I'm using an mdadm Raid5 with 4 disks.  When the labels change, I can't mount my Raid.

I changed the mount devices in my fstab from UUID labels to actual device labels /dev/sda1 /dev/sda2 and so on to see if I could force it to use the appropriate disks for the appropriate devices.  That didn't help so I went back to the UUID mount devices.

This is really annoying and I have forumed and googled myself half to death but couldn't find a solution.

As always, thanks in advance and any help would be greatly appreciated!

---

### Post by aoanla on 2008-10-04
All I can do is confirm that the disk mappings definitely change, apparently non-predictably, on boot, which appears to be why Ubuntu uses UUIDs by default in fstab.

I never managed to get consistent disk device mappings either.

---

### Post by xen-uno on 2008-10-04
Check your /media directory for duplicate mounts. I had ntfs partition dupes where a folder name was sd(x) and another was the volume's label name (ie xen-uno). They were both pointing to the same partition, which caused probs on bootup. I deleted all in /media except the cdrom(x)'s and folders matching valid volume names. I may have cleaned out fstab as well (don't recall) and changed a switch in Ubuntu somewhere which forces ntfs mounting on bootup. Finer details escape me ATM.

---

### Post by ariel on 2008-10-04
> **ddales said:**
> Hi all, I believe I have officially landed in Bizarro World!  Somehow, my disk mappings occasionally change on reboot.  I'm a pretty experienced Linux user and don't understand this at all.  

For example, my boot drive was originally /dev/sda.  But sometimes, after rebooting, the device labels change and my boot drive suddenly becomes /dev/sde which belongs to my Raid device.  WTF!?

This is a major problem because I'm using an mdadm Raid5 with 4 disks.  When the labels change, I can't mount my Raid.

I changed the mount devices in my fstab from UUID labels to actual device labels /dev/sda1 /dev/sda2 and so on to see if I could force it to use the appropriate disks for the appropriate devices.  That didn't help so I went back to the UUID mount devices.

This is really annoying and I have forumed and googled myself half to death but couldn't find a solution.

As always, thanks in advance and any help would be greatly appreciated!

I remember very well having this annoying problem in back in the feisty days. I could never find the cause; the problem vanished after a fresh install of feisty+1.

---

### Post by ddales on 2008-10-05
Well, I've gone back to UUIDs in the fstab and haven't experienced the problem again.  This is very funky.

---

### Post by ddales on 2008-10-08
I haven't found a way to statically map the devices but things seem to be Ok using the UUIDs.

---

