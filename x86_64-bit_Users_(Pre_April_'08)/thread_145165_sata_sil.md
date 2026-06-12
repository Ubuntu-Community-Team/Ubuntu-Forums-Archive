---
title: "sata_sil"
date: 2006-03-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by seventytwo on 2006-03-15
Good day!

Just got Ubuntu up and running on my G4. First time on Linux and I love it. All working nicely... apart from the fact that I can't configure to yaboot os x by default. The problem I have is that my os x installation is on a sata drive so I'm trying to set macosx=/dev/sda10. Unfortunately when I go to 'bless' this wby running ybin -v It tells me:

> ybin: Finding OpenFirmware device path to `/dev/sda10'...
ofpath: Driver: sata_sil is not supported
ybin: Unable to determine OpenFirmware path for macosx=/dev/sda10
ybin: Try specifying the real OpenFirmware path for macosx=/dev/sda10 in /etc/yaboot.conf

If I try to run ofpath /dev/sda I get the smae message about sata_sil not being supported.

I didn't have my SATA drive connected when I was installing ubuntu so I don't know if it missed the module/driver or something?

Any help is greatly appreciated, thanks. :D

---

### Post by staticdisaster on 2006-03-22
I ran into this problem too. I think the key is to get the OF path from OS X. run nvram -p to get the boot device. Something like this:

macosx=/pci@f2000000/pci-bridge@d/mac-io@7/ata-4@1f000/disk@0:2

---

