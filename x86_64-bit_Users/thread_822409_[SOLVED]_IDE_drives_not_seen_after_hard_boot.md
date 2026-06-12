---
title: "[SOLVED] IDE drives not seen after hard boot"
date: 2008-06-08
forum: x86 64-bit Users
---

### Post by ve3rpm on 2008-06-08
I'm not sure why, but I need to reset after I turn on my computer because neither of my 2 IDE drives are seen.  It kinda sucks have to boot twice.  Any ideas?  I'm not running dual boot.  Ubuntu is on my sata drive.

---

### Post by User3k on 2008-06-08
Have you checked you BIOS settings? I have two SATA and one IDE. The IDE is on master, channel 0 and the SATA's are on Channels 2 and 3 (or was it 4?)

I installed and un-installed a lot of different Linux and BSD OS's over the last few days. Had some time on my hands and a lot of free space to play with. Sometimes they would see my IDE as a SATA, so it would look like this. Sda, sdb and sdc (Which is my IDE.) But a few would also see it is hda. this really gave me a headache trying to install to the MBR, I never new where it would install it to, lol.

Do you have an 80 wire IDE conductor cable? Also do you have your IDE drives set at CS, (cable select?)

I am not sure if this helps at all.

---

### Post by ve3rpm on 2008-06-10
thanx I'll give it a whirl when I get home.

---

### Post by ddales on 2008-06-13
I've had a similar problem with a mix of IDE and SATA drives.  I still haven't found a decent solution though.

The problem that I'm having is renumeration of my drives after a reboot or updates, particularly after installing a new kernel.

I have a 200G IDE that contains my OS and 4x400G SATA drives that I configured into a RAID5 with mdadm.  Generally, my boot IDE is recognized as /dev/sda1 and my raid devices /dev/sd[b][c][d][e]1.  Sometimes though, and I'm not sure what is causing this, my drives get renamed after a reboot or updates.

My boot IDE gets renamed to /dev/sde1 and my SATA devices each get bumped down one letter to [a b c and d] which really confuses my mdadm.  I haven't suffered any data loss as a result of the renumeration but it's sometimes really annoying to have to reconfigure the mdadm.conf and restart the daemon.

---

### Post by ve3rpm on 2008-09-15
Well, I finally figured it out... I had to put a delay for the HDD in bios of 10 sec.  Now it's great.  Thanx for all the help!

---

