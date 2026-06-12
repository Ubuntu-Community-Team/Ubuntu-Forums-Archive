---
title: "install round 40 ?"
date: 2008-01-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by modelmark on 2008-01-06
I tried to install ubuntu 64 on my core duo, I'm about at round 40, day 3.
I had a lot of crashes during installation, mainly tune2fs. Searching lead me to believe there was a problem with the CD. I burned the CD several times, with verify never a problem, but I keep getting crashes. (tune2fs and mkfs.ext3)

To get it on a partition of a certain drive I chose manual for prepare disc space. I indicated the partition (format on) and the swap and proceeded. One time I actually pulled al the way through and was able to boot. Grub was no the wrong drive, so it booted straight into windows, but there is a way around it with the live CD.

I made the mistake to try and upgrade the driver of my EN85000GT video card. I lost my graphics with only a text interface, I decided to reinstall the whole thing from scratch. That is were it ended, I never got back to the installation. It always crashes on tune2fs and ignoring this will lead to mkfs.ext3 crashing during step 7.

What am I doing wrong ? Should I always use a complete disk and not just a partition for linux ? Or only a partition, if you let the linux  installer spit it off ? I wished I had made some sort of backup after the first install.
Maybe unplug all hard drives except the one used for linux ?

---

### Post by Kilz on 2008-01-06
> **modelmark said:**
> I tried to install ubuntu 64 on my core duo, I'm about at round 40, day 3.
I had a lot of crashes during installation, mainly tune2fs. Searching lead me to believe there was a problem with the CD. I burned the CD several times, with verify never a problem, but I keep getting crashes. (tune2fs and mkfs.ext3)

To get it on a partition of a certain drive I chose manual for prepare disc space. I indicated the partition (format on) and the swap and proceeded. One time I actually pulled al the way through and was able to boot. Grub was no the wrong drive, so it booted straight into windows, but there is a way around it with the live CD.

I made the mistake to try and upgrade the driver of my EN85000GT video card. I lost my graphics with only a text interface, I decided to reinstall the whole thing from scratch. That is were it ended, I never got back to the installation. It always crashes on tune2fs and ignoring this will lead to mkfs.ext3 crashing during step 7.

What am I doing wrong ? Should I always use a complete disk and not just a partition for linux ? Or only a partition, if you let the linux  installer spit it off ? I wished I had made some sort of backup after the first install.
Maybe unplug all hard drives except the one used for linux ?

Try the alternate install cd. Make sure the md5sum of the image matches [the md5sum]("http://mirrors.gigenet.com/ubuntu/7.10/MD5SUMS") to make sure the image file you downloaded is good. A partition is good. But you may want to delete the old attempts if any are there and not install over them.

---

