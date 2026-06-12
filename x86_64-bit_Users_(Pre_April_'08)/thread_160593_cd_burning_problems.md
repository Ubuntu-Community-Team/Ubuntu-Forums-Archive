---
title: "cd burning problems"
date: 2006-04-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Peter76 on 2006-04-15
Hello, the only thing that stopsmefrom completely switching to ubuntu is that I can't get cd burning to work properly. Under breezy the last program I tried was k3b, and that sometimes burned ok, but a lot of times not. Now just burned an audio cd in dapper with serpentine, it completely finished, but at the start of the process Igot these messages in my kernel.log:

Apr 15 14:26:43 ibook kernel: [ 6192.347762] ide-pmac lost interrupt, dma status: 8400
Apr 15 14:26:50 ibook kernel: [ 6192.347786] hda: lost interrupt
Apr 15 14:26:51 ibook kernel: [ 6192.347802] hda: dma_intr: status=0xd0 { Busy }Apr 15 14:26:51 ibook kernel: [ 6192.347815] ide: failed opcode was: unknown
Apr 15 14:26:51 ibook kernel: [ 6192.347834] hda: DMA disabled
Apr 15 14:26:51 ibook kernel: [ 6192.347845] hdb: DMA disabled
Apr 15 14:26:51 ibook kernel: [ 6192.395755] ide0: reset: success

and after this it burned the cd at an average of 4x while it should have been 24x.....
Also checking with hdparm showed that dma was turned of for both my hd and cdrom.... I think this is quite serious. Anyone having these problems? And should I file this as a bug? I'm going to delve deeper into the matter and post findings here... Any solutions for getting my cd burning to work properly are very welcome.

By the way, dma was on in breezy and dapper and I have an iBook 900 with 600MB ram

---

### Post by bscbrit on 2006-04-15
I use gnomebaker and it performs faultlessly with both CDs and DVDs.  You can always use 'hdparm' to re-configure your drives for the best I/O and then see if Dapper switches it off again.  That might give you some pointers as to what it happening.  Not heard of this problem before but, then, I spend most of my time in Breezy.

---

### Post by Peter76 on 2006-04-16
[QUOTE=bscbrit]I use gnomebaker and it performs faultlessly with both CDs and DVDs.  You can always use 'hdparm' to re-configure your drives for the best I/O and then see if Dapper switches it off again.  That might give you some pointers as to what it happening.  Not heard of this problem before but, then, I spend most of my time in Breezy.[/QUOTE]

I tried all different programs, but it all comes down to cdrecord anyway; but here something went seriously wrong.... After a reboot, burned the cd again, and now it finished allright again, but gave a scsi error about an unknown opcode at the start of the burning, and it slowly started to increase burn speed, but when tried to go faster than 16, it went back to 4x and stayed there:-( And my drive supports 24x
Anyone else has burn problems on iBooks????? Please report

---

### Post by Ptero-4 on 2006-04-17
Well. I had an iBook and can tell you that the built-in drive can be quite cocky at times. As for your issue. Your problem seems to be that ubuntu is shutting off DMA (the daemon that optimizes your optical and magnetical drive's performance) which by itself isn't fatal as long as your CD burning app detects it and reduces the writing speed to compensate (which by your description it's doing fine) and avoid buffer underruns (which happens when you try to write faster than the read speed, which empties your CD writer's internal buffer). The cause for that can be hardware incompatibilities. You can go to /var/log and check there your system logs to see what is going wrong.

---

### Post by Peter76 on 2006-04-17
[QUOTE=Ptero-4]Well. I had an iBook and can tell you that the built-in drive can be quite cocky at times. As for your issue. Your problem seems to be that ubuntu is shutting off DMA (the daemon that optimizes your optical and magnetical drive's performance) which by itself isn't fatal as long as your CD burning app detects it and reduces the writing speed to compensate (which by your description it's doing fine) and avoid buffer underruns (which happens when you try to write faster than the read speed, which empties your CD writer's internal buffer). The cause for that can be hardware incompatibilities. You can go to /var/log and check there your system logs to see what is going wrong.[/QUOTE]

Nice to hear that I'm not the only one with this problem. The error messages came fom the log, but show dma also going off for my harddisk, which really slowed down my system. I tried to reproduce the error, but then everything went fine. When looking through the cdrecord manpage, I came across the -immed and minbuf=flag, which can sort out problems when the cd and harddisk are on the same ide cable as in my situation. First time burning at full speed from the command line gave good results, but I'll have to do more testing. Tried to 'crash' the process by generating a lot of other disk i/o, which resulted in cdrecord slowing down, but by itself, which is good, but no things about dma disabled in my logs. 

Anyone who has this buggy cd burning on an iBook or other laptop or computer, please report and test with above mentioned flags! Would be nice to have this sorted out. Thanks, Peter

---

