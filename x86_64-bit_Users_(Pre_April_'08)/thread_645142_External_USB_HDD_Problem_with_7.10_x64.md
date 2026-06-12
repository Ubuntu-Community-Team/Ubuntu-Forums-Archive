---
title: "External USB HDD Problem with 7.10 x64"
date: 2007-12-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Dive4Life on 2007-12-19
When I plug in my external HDD Drive it mounts for a moment then it just disconnects. I ran a command I saw from another post and it gave me this output.

$ dmesg | tail
[ 434.721447] sd 143:0:0:0: [sdc] Mode Sense: 00 38 00 00
[ 434.721451] sd 143:0:0:0: [sdc] Assuming drive cache: write through
[ 434.721454] sdc: sdc1
[ 434.724406] sd 143:0:0:0: [sdc] Attached SCSI disk
[ 434.724452] sd 143:0:0:0: Attached scsi generic sg2 type 0
[ 434.966029] kjournald starting. Commit interval 5 seconds
[ 434.966784] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[ 434.970875] EXT3 FS on sdc1, internal journal
[ 434.970878] EXT3-fs: recovery complete.
[ 434.970974] EXT3-fs: mounted filesystem with ordered data mode.

Thanks for your time and I hope there is a fix for this.

---

### Post by mips on 2007-12-20
> **Dive4Life said:**
> 
[ 434.966784] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended


Do what it says.

---

### Post by Dive4Life on 2007-12-20
Sounds much easier said than done.  I am definitely a noob and can't seem to figure out how to execute that command.  Thanks for your time.

---

### Post by logos34 on 2007-12-20
sudo fsck /dev/sdc1

---

