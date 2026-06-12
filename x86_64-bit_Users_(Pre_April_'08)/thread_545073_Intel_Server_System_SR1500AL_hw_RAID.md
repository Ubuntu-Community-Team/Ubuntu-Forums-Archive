---
title: "Intel Server System SR1500AL hw RAID"
date: 2007-09-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by rihad on 2007-09-07
Hi, I'm trying to install ubuntu-7.04-server-amd64 on Intel Server System SR1500AL. The board has two 500 gig SCSI drives set up in a RAID1 in the BIOS. The array isn't recognized by Ubuntu setup, which instead shows them as two separate SCSI disks. Any way to fix this? Thanks.

---

### Post by John.Michael.Kane on 2007-09-07
For setting up raid you can look into one or all of the guides below.
[HOWTO: Linux Software Raid using mdadm]("http://ubuntuforums.org/showthread.php?t=408461&highlight=raid")
[RAID]("https://wiki.ubuntu.com/Raid?highlight=%28raid%29")
[Installation/RAID1]("https://help.ubuntu.com/community/Installation/RAID1")
[Howto: Create RAID]("http://ubuntuforums.org/showthread.php?t=517282&highlight=raid")

---

### Post by rihad on 2007-09-07
Thanks, but shouldn't hardware RAID "just work"? Or do I need to set up mdadm for hardware RAID too? I don't think so. I'm more concerned with a probable lack of Intel driver for Linux... anyone who's had experience with this?

---

### Post by John.Michael.Kane on 2007-09-07
> **rihad said:**
> Thanks, but shouldn't hardware RAID "just work"? Or do I need to set up mdadm for hardware RAID too? I don't think so. I'm more concerned with a probable lack of Intel driver for Linux... anyone who's had experience with this?

First off your board is using the ESB2 SATA Controller which is a software/BIOS based RAID. RAID 0, 1, and 10solution. 

Thus the reason for the links posted.

---

### Post by rihad on 2007-09-08
I've two twin boards: one uses SATA RAID1,  the other one SAS RAID1. Neither can be detected by Ubuntu/FreeBSD.

Thanks for the clarification, I really thought this board expensive as hell *must* have hardware raid. Ok, off I go to do software raid... thanks again.

---

