---
title: "GRUB Loading stage1.5 Loop"
date: 2006-04-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by bper on 2006-04-01
Hi, 

I've checked the forum for similar posts, the one similar that I saw got no response. Anyway, I just built my pc with the specs below (didn't mention the dvd drives, etc.). After downloading and installing the AMD64 version of Breezy I got the message listed in the title of this post, continuously in a loop.

After looking at the forums, I attempted to manually configure my partitions, but the same problem occurs. My RAID array is configured in the hardware, not the software. What could be causing this problem? Any ideas?

---

### Post by bper on 2006-04-02
OK, seems to be related to my hardware raid configuration or partitioning.

I removed my raid configuration, repartitioned the first hard drive manually, and Breezy installed and booted perfectly.

When I cleaned everything again, and tried to configure hardware raid, problems returned.

I will try software raid configuration and see how this works.

I don't know if this will help anyone, but this is what I'm discovering as I go along.

---

### Post by bper on 2006-04-03
OK,

The problem is definitely with the hardware RAID configuration. Grub is not recognizing the boot partition in the RAID configuration. I will check for posts on this subject in this forum and others while trying to figure this out. 

If any one has any ideas, or know of any links or past posts on the subject I'd appreciate it if you'd let me know.

Thanks.

---

### Post by NewbieNik on 2006-04-03
Never used a SATA rais, but on older SCSI2 RAIDs I had to set noapic and aic=7xxx switches on the install. Also set aside a boot partition of 500Mb.
Worked really well on older RAID server (HP Netserver LH-pro and LH4)

---

