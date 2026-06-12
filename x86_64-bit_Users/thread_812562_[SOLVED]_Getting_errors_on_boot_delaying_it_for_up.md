---
title: "[SOLVED] Getting errors on boot delaying it for up to 10 minutes.  New install"
date: 2008-05-30
forum: x86 64-bit Users
---

### Post by schapp on 2008-05-30
Hi all,

I installed Ubuntu in my new HP dv2000 series system and ran like a breeze.  However, I needed to install Vista for wife purposes.  I installed Vista wiping out Ubuntu and then install Ubuntu again.   From that time... I've been getting errors every time the system boots.  It appears that it's pointing out to disk issues but I doubt it's the case in here, so I need some guidance from the experts.

These are the errors:

```

May 30 00:24:41 Endor-Ubuntu kernel: [   34.829460] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May 30 00:24:41 Endor-Ubuntu kernel: [   34.829465] ata3.00: irq_stat 0x40000001
May 30 00:24:41 Endor-Ubuntu kernel: [   34.829471] ata3.00: cmd 25/00:20:4a:f8:df/00:00:1c:00:00/e0 tag 0 dma 16384 in
May 30 00:24:41 Endor-Ubuntu kernel: [   34.829472]          res 51/40:00:5d:f8:df/00:00:1c:00:00/e0 Emask 0x9 (media error)
May 30 00:24:41 Endor-Ubuntu kernel: [   34.829476] ata3.00: status: { DRDY ERR }
May 30 00:24:41 Endor-Ubuntu kernel: [   34.829478] ata3.00: error: { UNC }
May 30 00:24:41 Endor-Ubuntu kernel: [   34.830745] ata3.00: configured for UDMA/100
May 30 00:24:41 Endor-Ubuntu kernel: [   34.830753] ata3: EH complete
May 30 00:24:41 Endor-Ubuntu kernel: [   42.331728] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May 30 00:24:41 Endor-Ubuntu kernel: [   42.331733] ata3.00: irq_stat 0x40000001
May 30 00:24:41 Endor-Ubuntu kernel: [   42.331738] ata3.00: cmd 25/00:20:4a:f8:df/00:00:1c:00:00/e0 tag 0 dma 16384 in
May 30 00:24:41 Endor-Ubuntu kernel: [   42.331740]          res 51/40:00:67:f8:df/00:00:1c:00:00/e0 Emask 0x9 (media error)
May 30 00:24:41 Endor-Ubuntu kernel: [   42.331742] ata3.00: status: { DRDY ERR }
May 30 00:24:41 Endor-Ubuntu kernel: [   42.331744] ata3.00: error: { UNC }
May 30 00:24:41 Endor-Ubuntu kernel: [   42.333063] ata3.00: configured for UDMA/100
May 30 00:24:41 Endor-Ubuntu kernel: [   42.333073] ata3: EH complete
May 30 00:24:41 Endor-Ubuntu kernel: [   49.834295] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May 30 00:24:41 Endor-Ubuntu kernel: [   49.834300] ata3.00: irq_stat 0x40000001
May 30 00:24:41 Endor-Ubuntu kernel: [   49.834305] ata3.00: cmd 25/00:20:4a:f8:df/00:00:1c:00:00/e0 tag 0 dma 16384 in
May 30 00:24:41 Endor-Ubuntu kernel: [   49.834307]          res 51/40:00:67:f8:df/00:00:1c:00:00/e0 Emask 0x9 (media error)
May 30 00:24:41 Endor-Ubuntu kernel: [   49.834309] ata3.00: status: { DRDY ERR }
May 30 00:24:41 Endor-Ubuntu kernel: [   49.834311] ata3.00: error: { UNC }
May 30 00:24:41 Endor-Ubuntu kernel: [   49.835618] ata3.00: configured for UDMA/100
May 30 00:24:41 Endor-Ubuntu kernel: [   49.835628] ata3: EH complete
May 30 00:24:41 Endor-Ubuntu kernel: [   53.972622] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May 30 00:24:41 Endor-Ubuntu kernel: [   53.972627] ata3.00: irq_stat 0x40000001
May 30 00:24:41 Endor-Ubuntu kernel: [   53.972632] ata3.00: cmd 25/00:20:4a:f8:df/00:00:1c:00:00/e0 tag 0 dma 16384 in
May 30 00:24:41 Endor-Ubuntu kernel: [   53.972634]          res 51/40:00:58:f8:df/00:00:1c:00:00/e0 Emask 0x9 (media error)
May 30 00:24:41 Endor-Ubuntu kernel: [   53.972636] ata3.00: status: { DRDY ERR }
May 30 00:24:41 Endor-Ubuntu kernel: [   53.972638] ata3.00: error: { UNC }
May 30 00:24:41 Endor-Ubuntu kernel: [   53.973937] ata3.00: configured for UDMA/100
May 30 00:24:41 Endor-Ubuntu kernel: [   53.973947] ata3: EH complete
May 30 00:24:41 Endor-Ubuntu kernel: [   56.886271] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
May 30 00:24:41 Endor-Ubuntu kernel: [   56.886275] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
May 30 00:24:41 Endor-Ubuntu kernel: [   56.892450] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
May 30 00:24:41 Endor-Ubuntu kernel: [   56.892452] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
May 30 00:24:41 Endor-Ubuntu kernel: [   60.131117] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May 30 00:24:41 Endor-Ubuntu kernel: [   60.131122] ata3.00: irq_stat 0x40000001
May 30 00:24:41 Endor-Ubuntu kernel: [   60.131127] ata3.00: cmd 25/00:20:4a:f8:df/00:00:1c:00:00/e0 tag 0 dma 16384 in
May 30 00:24:41 Endor-Ubuntu kernel: [   60.131128]          res 51/40:00:67:f8:df/00:00:1c:00:00/e0 Emask 0x9 (media error)
May 30 00:24:41 Endor-Ubuntu kernel: [   60.131131] ata3.00: status: { DRDY ERR }
May 30 00:24:41 Endor-Ubuntu kernel: [   60.131133] ata3.00: error: { UNC }
May 30 00:24:41 Endor-Ubuntu kernel: [   60.132406] ata3.00: configured for UDMA/100
May 30 00:24:41 Endor-Ubuntu kernel: [   60.132416] ata3: EH complete
May 30 00:24:41 Endor-Ubuntu kernel: [   66.657955] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
May 30 00:24:41 Endor-Ubuntu kernel: [   66.657960] ata3.00: irq_stat 0x40000001
May 30 00:24:41 Endor-Ubuntu kernel: [   66.657965] ata3.00: cmd 25/00:20:4a:f8:df/00:00:1c:00:00/e0 tag 0 dma 16384 in
May 30 00:24:41 Endor-Ubuntu kernel: [   66.657967]          res 51/40:00:67:f8:df/00:00:1c:00:00/e0 Emask 0x9 (media error)
May 30 00:24:41 Endor-Ubuntu kernel: [   66.657969] ata3.00: status: { DRDY ERR }
May 30 00:24:41 Endor-Ubuntu kernel: [   66.657971] ata3.00: error: { UNC }
May 30 00:24:41 Endor-Ubuntu kernel: [   66.659257] ata3.00: configured for UDMA/100
May 30 00:24:41 Endor-Ubuntu kernel: [   66.659290] sd 2:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
May 30 00:24:41 Endor-Ubuntu kernel: [   66.659295] sd 2:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
May 30 00:24:41 Endor-Ubuntu kernel: [   66.659299] Descriptor sense data with sense descriptors (in hex):
May 30 00:24:41 Endor-Ubuntu kernel: [   66.659300]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
May 30 00:24:41 Endor-Ubuntu kernel: [   66.659306]         1c df f8 67 
May 30 00:24:41 Endor-Ubuntu kernel: [   66.659309] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
May 30 00:24:41 Endor-Ubuntu kernel: [   66.659314] end_request: I/O error, dev sda, sector 484440167
May 30 00:24:41 Endor-Ubuntu kernel: [   66.659317] Buffer I/O error on device sda6, logical block 29
May 30 00:24:41 Endor-Ubuntu kernel: [   66.659320] Buffer I/O error on device sda6, logical block 30
May 30 00:24:41 Endor-Ubuntu kernel: [   66.659323] Buffer I/O error on device sda6, logical block 31
May 30 00:24:41 Endor-Ubuntu kernel: [   66.659339] ata3: EH complete
May 30 00:24:41 Endor-Ubuntu kernel: [  102.720510] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
May 30 00:24:41 Endor-Ubuntu kernel: [  102.760241] sd 2:0:0:0: [sda] Write Protect is off
May 30 00:24:41 Endor-Ubuntu kernel: [  102.760243] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
May 30 00:24:41 Endor-Ubuntu kernel: [  102.766650] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 30 00:24:41 Endor-Ubuntu kernel: [  102.766668] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
May 30 00:24:41 Endor-Ubuntu kernel: [  102.766677] sd 2:0:0:0: [sda] Write Protect is off
May 30 00:24:41 Endor-Ubuntu kernel: [  102.766680] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
May 30 00:24:41 Endor-Ubuntu kernel: [  102.775211] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

These errors repeat for a couple of times and the system can take up to 10 minutes to boot!

Config:  TL-62, 4Gb, 250Gb HD.

Any help will be more than welcome.   I already searched the forums for help but couldn't find anything conclusive.


Thanks!

---

### Post by bford16 on 2008-05-30
Do you have an SATA drive?  Hardy has a kernel bug that prevents it from recognizing SATA drives correctly.  See: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209454](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/209454)

---

### Post by schapp on 2008-06-05
bford16:

Thanks for pointing me out to that document.  Installing kernel 2.6.24-18 apparently solved the problem.

Sorry to take this long to reply, I've been on the road lately.

Thanks again!

---

### Post by mushroomcloudwarrior on 2008-10-12
> **schapp said:**
> bford16:

Thanks for pointing me out to that document.  Installing kernel 2.6.24-18 apparently solved the problem.

Sorry to take this long to reply, I've been on the road lately.

Thanks again!

I'm having the exact same problem as you are. 

I'm running a dual booting Dell inspiron 1500, with Ubuntu Hardy 8.04. I seem to have randomly gotten this problem. I'm only a beginner, and don't know much about Linux or Unix. 

Any help will be deeply appreciated!

---

### Post by reya276 on 2009-01-18
Same issue here with my Dell XPS m1330, I was also running hardy. This happen after an update. The funny thing is that I reformatted my disk and install intrepid but the same errors ata3: drdy err crap. What the hell is going on?

---

### Post by BrooksOfSheffield on 2009-01-27
I started having a similar problem a couple of days ago.

Apparently having blank media in my optical drive at bootup was a problem.

YMMV

---

### Post by painejake on 2009-01-28
I had this issue on my recent build (Not quite same error msg). Turned out to be my SATA DVD+RW DL drive. Only had them on the first boot though on 8.10 ;)

---

