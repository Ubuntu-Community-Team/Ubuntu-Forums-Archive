---
title: "Ubuntu 7.04 Crashing- nVidia MB Chipset"
date: 2007-07-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by onering on 2007-07-14
My PC has the following hardware:
Ubuntu 7.04 x86_64, 
CPU:AMD64 X2 3600+, 
RAM:2GB DDR2 667, 
VIDEO:nVidia 7300 GS, 
MothBoard:ECS GeForce6100SM-M, nVidia MCP61 Chipset, 
PVR-150(not yet working in Ubuntu)

After using this newly built PC for about a week, I'm getting lock-up crashes and applications that close for no reason.  This happens under light of heavy CPU load every few hours of usage.  Restarting the PC fixes things.

This is the first time I'm using the 64 bit version of Ubuntu, and the first time I'm using an nVidia motherboard chipset.  Not sure if this is related to compatibility issues with Ubuntu and the nVidia motherboard chipset?

1) Are there any Linux log files that I could look at during or post one of these crash events that could give me a clue as to what is going on?
2) Does anyone have experience with ths Motherboard and the MCP61 Chipset?

Thanks.

---

### Post by xzero1 on 2007-08-28
Check System->Administration->System Logs. I would check for a memory and/or a heat issue. I have had a similar issue and it turned out to be a memory timing problem. Only during high cpu load would the problem occur. Run memtest86 (bootup option) for a couple of hours to check memory issues.

---

