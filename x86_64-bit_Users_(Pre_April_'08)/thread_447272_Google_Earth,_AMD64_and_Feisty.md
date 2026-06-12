---
title: "Google Earth, AMD64 and Feisty"
date: 2007-05-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by OldSeaDog on 2007-05-17
There were several people having problems in the fall, but I couldn't find a recent post, so...

I am running Feisty and tried to run the Google Earth installer GoogleEarthLinux.bin, version 4.1.  I don't know whether it is Feisty, the AMD64 processor and 32 bit code, the new NVidia driver or what, but it starts the integrity check and uncompression, then it bombs.  I have downloaded 3 different copies - same result, as follows-

sh GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.1.7076.4458..........................................................................
./setup.sh: 284: setup.data/bin/Linux/amd64/setup.gtk2: not found
./setup.sh: 299: setup.data/bin/Linux/amd64/setup.gtk: not found
The setup program seems to have failed on amd64

Fatal error, installer failed to run at all

I have seen suggestions that it may be necessary to set up a 32 bit emulator to run it in.  Hopefully there is a solution.  It ran fine under Edgy.

For information purposes I have an ASUS 64X2 4200+ motherboard/processor with 2 GB of RAM, an NVidia 7600 video card, a SATA 320 GB drive, and IDE 250 GB drive and the usual combination of external devices, Ethernet connections, etc.

---

### Post by Case_f on 2007-05-17
Did you install ia32-libs-gtk package?

---

### Post by nss0000 on 2007-05-18
OSD:

I'm running similar kit ( amd5400/ASUS-m2n ) , and with Dapperx64 found GoogleEarth automagically installed/runs without issue. When I queried howcome an n.g.member suggested GOOGLE is deploying for x64UBUNTU a "static" G.E. with all required support 'internal'.

Acts like it with my x64Dapper. Maybe 'flouzyFawn' is just flakey.

nss
*******

---

