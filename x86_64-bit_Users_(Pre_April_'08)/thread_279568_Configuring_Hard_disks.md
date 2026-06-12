---
title: "Configuring Hard disks"
date: 2006-10-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by cocteau on 2006-10-18
Hi

I think I need to do some work to configure my hard drives. When I copy larger files (500 MB+) it seems to hang and then copy a great deal in a burst before it stops again. And sometimes it will give me a disk I/O error. However if I skip the file I can copy it later without problems.

This only seem to happen when I copy from my external USB 2.0 drive to my SATA hard drive but I have no idea where to start and look for a solution to this problem.

Any suggestions?

---

### Post by Jussi Kukkonen on 2006-10-18
Check if anything comes up in logs in /var/log/, possibly /var/log/messages, when that happens.

---

### Post by jamal07 on 2006-10-19
> **cocteau said:**
> Hi

I think I need to do some work to configure my hard drives. When I copy larger files (500 MB+) it seems to hang and then copy a great deal in a burst before it stops again. And sometimes it will give me a disk I/O error. However if I skip the file I can copy it later without problems.

This only seem to happen when I copy from my external USB 2.0 drive to my SATA hard drive but I have no idea where to start and look for a solution to this problem.

Any suggestions?

I have had similar situation. I had problem with laptop harddisk, OS did not seem to enable DMA for it properly, after I enabled DMA all worked great.

As Jussi suggested, check logs (check them for DriveSeek errors).

[http://mr.uue.org/gnulinux/t20/](http://mr.uue.org/gnulinux/t20/)

Section "Hard disk drive" gives some guidance about updating harddisk settings (enabling DMA etc.)

Check your DMA settings is my [put here amount of character].

rgrds,
JeiMal

---

### Post by cocteau on 2006-10-19
Cool. Points to the both of you :)

I don't know which log to specifically look for in /var/log but /var/log/messages had two types of errors which seems to be alarmingly common on my system.

usb 5-3: reset high speed USB device using ehci_hcd and address 7
sdf: Current: sense key: No Sense
   Additional sense: No additional sense information

and

sdf5: rw=0, want=258273032, limit=225279432
attempt to access beyond end of device

Furthermore the hdparm command fails as it seems like the kernel is treating the usb drive as a scsi drive but mounting it on /dev/sdf.

Any suggestions?

---

