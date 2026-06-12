---
title: "Ubuntu freezes (64bit)"
date: 2006-10-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by henk_z on 2006-10-31
Hi people,

My latest Ubuntu 64-bit version randomly freezes. Now i had this before with Windows XP and the trick was to uninstall the AMD 64-bit processor drivers. Since then i had no problems in windows. But now i've started to use Ubuntu i have the same problem (atleast it looks like the same problem) in Ubuntu. 

Anyone knows what to try? I checked if there were any amd drivers in the install but it seems there aren't any. I don't know what it could be, i'm thinking that it's the same problem i had with windows but i'm not sure. Maybe anyone here knows another source.

Any help is appreciated!

System:

Acer Aspire 1500
ATI Radeon Mobility 9600
AMD Ahtlon 64 bit 3000+
512MB Mem

SWAP partition: 1.5 GB

---

### Post by Marvil on 2006-10-31
Hi henk_z 
The most common reason for PCs to hang. 

1. Problem with powersupply 
2. Heat in the system probably bios shuts down PC(specially with Laptops) 
3. memory is failing
4. Graphics card hangs with wrong drivers.

If you had the same problem , you could clock the time when you start the PC and the hang. This could give you a clue if it is almost the same time, because you do usually the same thing when you start a PC. 

Cheers Marvil  ;)

---

### Post by kuja on 2006-11-01
My bet's on the graphics card drivers.

---

### Post by henk_z on 2006-11-01
Well, i tried some things but it seems that the system randomly crashes (sometimes after 20mins or sometimes after 1 1/2 hour). 

I noticed that when ubuntu freezes my harddisk 'busy led' keeps on so it seems that the harddisk goes crazy when it happens.... But i don't think it's my harddisk cause in Windows i do not have this freezing problem (anymore, after removing amd 64 drivers). Maybe its the partition settings or something? I installed Ubuntu with the following partition settings:

40MB ext2 /Boot
5GB ext3 /
5GB ext3 /home
1.5GB linux-swap /swap

Are these correct settings for an installation?

---

