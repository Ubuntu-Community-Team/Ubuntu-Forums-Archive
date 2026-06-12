---
title: "System hang on SDCard copy operation"
date: 2009-03-05
forum: x86 64-bit Users
---

### Post by gobble on 2009-03-05
Hello

My system hung twice needing reboots when copying photos from my camera SDCard to foler. Thunar was at 99%. 

Various messages I saw in the logs include:

----------------------
Mar  5 10:23:52 owl kernel: ice
Mar  5 10:23:52 owl kernel: <ice
Mar  5 10:23:52 owl last message repeated 56 times
Mar  5 10:23:52 owl kernel: <iffflinfflinfflifflinfflfflinfflinfflinfflinfflifflinfflinfflifflifflinfflifflifflifflifflifflifflin
fflfflifflifflifflifflifflifflinfflifflifflifflifflifflifflifflifflifflifflifflifflifflifflifflifflifflifflifflifflifflifflifflif
fliffliffliffliffliffliffliffline devicefflinfflifflinfflfflifflifflifflifflifflifflifflifflifflifflifflifflifflifflinffliffliffl
iffflinfflinfflifflifflifflifflifflifflifflinfflfflifflinfflifflifflifflifflifflifflifflinfflifflifflifflinfflifflifflifflinfflif
flifflifflinfflifflifflifflifflifflifflifflifflifflinfflfflifflifflifflifflifflifflifflifflifflifflinfflinfflinfflfflifflifflifff
flifflifflinfflfflifflifflinfflinffliffliffliffliffliffliffliffliffffliffliffliffliffliffliffliffliffliffliffliffliffliffliffliff
lifflifflifflifflifflifflifflifflifflifflifflifflifflifflifflifflifflifflifflinfflifflifflinfflifflifflifflifflifflifflifflifflin
fflfflifflinfflifflifflifflifflifflifflifflifflifflinfflfflinfflifflifflifflifflinffliffliffliffliffliffliffliffliffliff
Mar  5 10:23:52 owl kernel: lifflinfflinfflifflinfflifflifflifflifflifflifflifflifffflifflifflifflifflifflifflifflifflifflifflinf
flifflifflifflifflifflinfflifflifflinfflifflinfflinfflfflifflifflifflifflinfflifflifflinfflfflifflifflifflifflifflifflifflinfflff
linfflfflifflifflifflifflifflifflifflifflifffflifflifflifflifflifflifflifflifflifflinfflifflifflifflifflifflifflinfflffliffliffff
lifflifflifflifflifflifflifflifflifflinfflifflinfflfflifflifflifflifflifflifflifflifflifflifflinfflifflifflinfflfflifflifflifflif
flifflinfflifflifflifflifflifflifflifflifflifflinfflfffflifflifflifflifflifflifflifflifflinffliffliffliffliffliffliffliffliffliff
lifflifffflifflifflifflifflifflifflifflifflifflifflifflifflinfflinfflfflifflfflifflinfflifflinffliffliffliffliffliffliffliffliffl
ifflifflifflifflifflifflifflifffflifflifflinfflfflifflinfflifflinfflifflinfflfflinfflfflinfflinffliffliffliffliffliffliffliffliff
lifflifflifflifflifflinefflifflifflifflifflifflinfflifflinfflifflifflifffflifflifflinfflifflifflinfflfflifflinffliffliff
Mar  5 10:23:52 owl kernel: lifflifflifflifffflinfflifflifflifflifflifflifflifflinfflifflifflifffflifflifflifflifflifflifflifflin
ffliffliffliffliffliffliffliffliffliffliffliffliffliffliffliffliffliffliffliffliffliffliffliffliffliffliffliffliffffliffliffliffl
ifflifflifflifflifflifflifflifflifflifflifflifflifflifflifflifflifflinfflifflifflifflinfflifflifflifflinfflifflifflinffflifflinff
linfflfflifflifflifflifflifflifflifflifflifflinfflifflifflifflifflifflifflinfflifflinfffflifflinfflifffflinfflinfflifflinfflinffl
infflifflifflinfflifflifflinfflfflinfflinfflinfflinfflifflifflinfflinfflifflinfflifflinfflinfflinfflinfflinfflinfflifflinffliffli
nfflifflifflinfflinfflinfflinfflinfflinfflinfflinfflfflinfflinfflfflinfflinfflifflifflifflinfflinfflifflifflinfflifflifflifffflif
flifflifflinfflinfflifflinffliffliffline devifflinfffflinfflifflifflifflinfflifflinfflinfflinfflifflinfflinfflinfflifflinfflinffl
infflifflinfflinfflinfflinfflinfflinfflfflinfflinfflifflifflifflifflifffflinfflinfflinfflinfflinfflifflifflifflinffliffl
Mar  5 10:23:52 owl kernel: lifflifflinfflinfflifflifflinfflifflifflifflinfflinfflifflinfflinfflinfflifflinfflifflifflifflinfflin
fflifflinfflifflinfflinfflinfflinfflifflifflifflinfflifflinfflifflinfflinfflfflifflinfflfflinfflifflinefflifflinfflinfflifflinffl
infflinffflinfflifflifflinfflinfflifflifflifflinfflinfflinfflifflinfflinfflinfflifflinfflinfflinfflinfflinfflifflinfflinfflifflif
flinfflinfflinfflinfflinfflinfflinfflinfflinfflinfflinfflinfflinfflifflinfflinfflfflinfflinfflinfflifflifflinfflifflifflinfflinff
linfflifflinfflinfflinfflinfflinfflinfflinfflifflifflinfflinfflifflinfflinfflinfflinfflinffflinfflinfflinfflinfflinfflinfflifflinfflinfflinfflfflinfflinfflifflifflinfflinfflinfflifflinfflinefflinfflinfflinfflifflinfflifflifffflinfflinfflinfflifflinfflinfflinfflinfflinfflifflifflinfflifflifflifflifffflifflinfflifflinfflinfflinfflinfflinfflinfflinfflifflifflinfflifflinfflinfflinfflinfflfflinfflinefflinfflinfflifflinfflinfflifflinfflinfflinfflinfflifflinfflinfflfflinfflinefflinfflifflinfflifflinffliffliff
Mar  5 10:23:52 owl kernel: linfflinfflifflinfflinfflifflinfflinfflinfflifflinfflifflifflifflifflifflinfflifflinfflinfflifflifflificeice
Mar  5 10:23:52 owl kernel: <ice
Mar  5 10:23:52 owl last message repeated 2 times
Mar  5 10:23:52 owl kernel: ice
-------------------------
[   78.242183]  sdd: sdd1
[  198.220417] hub 5-4.1:1.0: cannot reset port 1 (err = -110)
[  198.703100] hub 5-4.1:1.0: cannot reset port 1 (err = -110)
[  199.183041] hub 5-4.1:1.0: cannot reset port 1 (err = -110)
[  199.664345] hub 5-4.1:1.0: cannot reset port 1 (err = -110)
[  200.145631] hub 5-4.1:1.0: cannot reset port 1 (err = -110)
[  200.145639] hub 5-4.1:1.0: Cannot enable port 1.  Maybe the USB cable is bad?
[  200.626929] hub 5-4.1:1.0: cannot disable port 1 (err = -110)


[  443.353562] sd 6:0:0:1: rejecting I/O to offline device
[  443.353568] sd 6:0:0:1: rejecting I/O to offline device
[  443.353573] sd 6:0:0:1: rejecting I/O to offline device
-----------------------

The card reader is built-in in the DELL 2408WFP monitor:
-----------------------------
Mar  5 10:04:54 owl kernel: [   45.866039] scsi 6:0:0:0: Direct-Access     Generic  Flash HS-CF      5.39 PQ: 0 ANSI: 0
Mar  5 10:04:54 owl kernel: [   45.867516] scsi 6:0:0:1: Direct-Access     Generic  Flash HS-COMBO   5.39 PQ: 0 ANSI: 0
Mar  5 10:04:54 owl kernel: [   45.871440] sd 6:0:0:0: [sdc] Attached SCSI removable disk
Mar  5 10:04:54 owl kernel: [   45.871479] sd 6:0:0:0: Attached scsi generic sg2 type 0
Mar  5 10:04:54 owl kernel: [   45.929515] sd 6:0:0:1: [sdd] 3970048 512-byte hardware sectors (2033 MB)
Mar  5 10:04:54 owl kernel: [   45.933793] sd 6:0:0:1: [sdd] Write Protect is off
Mar  5 10:04:54 owl kernel: [   45.946930] sd 6:0:0:1: [sdd] 3970048 512-byte hardware sectors (2033 MB)
Mar  5 10:04:54 owl kernel: [   45.949549] sd 6:0:0:1: [sdd] Write Protect is off
Mar  5 10:04:54 owl kernel: [   45.953368]  sdd: sdd1
Mar  5 10:04:54 owl kernel: [   45.955439] sd 6:0:0:1: [sdd] Attached SCSI removable disk
Mar  5 10:04:54 owl kernel: [   45.955483] sd 6:0:0:1: Attached scsi generic sg3 type 0

-------------------------------
XUbuntu 8.0.4.2
2.6.24-23-generic #1 SMP Mon Jan 26 01:04:16 UTC 2009 x86_64 GNU/Linux
AMD 780G chipset.

Should I open a CR for this? lspci output attached.

TIA
Regards

---

### Post by gobble on 2009-03-05
I think it is due to this bug?

[https://bugs.launchpad.net/ubuntu/+bug/321207](https://bugs.launchpad.net/ubuntu/+bug/321207)

I also recall seeing the "FAT: Directory bread(block xxxx) failed" error.

Regards

---

### Post by gobble on 2009-03-05
This seems to have fixed it:

sudo sh -c "echo 120 > /sys/block/sda/queue/max_sectors_kb"

Any idea what it does? And why it fixed it?

Regards

---

