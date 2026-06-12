---
title: "2nd SATA Drive"
date: 2007-06-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by phoch_00 on 2007-06-03
Recently my second SATA drive disappeared. I'm guessing it happened after a kernel update but I'm not positive. I don't use the drive regularly but I went to pull something off of it and it failed. I get messages in the logs on boot like:

Jun  3 11:45:06 mypc kernel: [   29.785740] ATA: abnormal status 0x7F on port 0x000000000001e207
Jun  3 11:45:06 mypc kernel: [   29.796323] ATA: abnormal status 0x7F on port 0x000000000001e207
Jun  3 11:45:06 mypc kernel: [   29.807543] ata2.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 0
Jun  3 11:45:06 mypc kernel: [   29.807777] ata2.00: limiting speed to UDMA/133:PIO3
Jun  3 11:45:06 mypc kernel: [   35.010377] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun  3 11:45:06 mypc kernel: [   35.176771] ATA: abnormal status 0x7F on port 0x000000000001e207
Jun  3 11:45:06 mypc kernel: [   35.187357] ATA: abnormal status 0x7F on port 0x000000000001e207
Jun  3 11:45:06 mypc kernel: [   35.198632] ata2.00: ata_hpa_resize 1: sectors = 976773168, hpa_sectors = 0
Jun  3 11:45:06 mypc kernel: [   35.198862] ata2.00: disabled

I have had this setup for quite some time and both  sda and sdb are configured exactly the same as they are both identical drives. sda works fine but sdb is just gone. It doesn't show up in gparted and I can't mount it. I've searched the web a bit and it seems like others have this issue and it's related to the kernel in some way but I haven't found a way to fix it. Any help?

Running 7.04 2.6.20-16-generic #2 SMP x86_64 GNU/Linux

---

### Post by kuja on 2007-06-04
I recommend moving back to an older kernel if it's kernel related.  So long as all of your hardware works it really doesn't matter what version of kernel you use anyway ... Heck, I'm still using 2.6.18 :)

---

### Post by phoch_00 on 2007-06-09
It turns out the drive had really gone bad. I read somewhere to try a "cold" boot and when I did, the BIOS didn't detect the drive and when it started to spin up it made some pretty horrible clicking noises. I tried the "freezer" trick - put the drive in the freezer for a bit to see if I could get it to spin one last time but no luck. It's now a 500Gb paperweight on my desk. The drive is less than a year old. I'm not real happy.

---

### Post by crjackson on 2007-06-09
> **phoch_00 said:**
> It turns out the drive had really gone bad. I read somewhere to try a "cold" boot and when I did, the BIOS didn't detect the drive and when it started to spin up it made some pretty horrible clicking noises. I tried the "freezer" trick - put the drive in the freezer for a bit to see if I could get it to spin one last time but no luck. It's now a 500Gb paperweight on my desk. The drive is less than a year old. I'm not real happy.

Man I hate it when that happens.  I have 2 of those paperweights - MAXTOR's no more...

---

