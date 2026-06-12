---
title: "DVD Burning issues"
date: 2006-07-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by professor_b on 2006-07-22
I'm trying to burn an .img file. 

K3b recognizes and checksums the file as an ISO, but when I go to burn, it complains that the media I'm using isn't a recordable DVD. Okay, so I try it on the command line with growisofs and get the same error. I have the same problem in gnomebaker. (and by the way, I can burn the image just fine on my mac, with the same media that k3b says isn't media).

Here's some output from the logs:

```

Jul 22 18:26:09 localhost kernel: [79688.263582] hda: irq timeout: status=0xd0 { Busy }
Jul 22 18:26:09 localhost kernel: [79688.263584] ide: failed opcode was: unknown
Jul 22 18:26:09 localhost kernel: [79688.263588] hda: DMA disabled
Jul 22 18:26:23 localhost kernel: [79694.921049] hda: ATAPI reset complete
Jul 22 18:37:07 localhost -- MARK --
Jul 22 18:40:35 localhost kernel: [80136.635687] ide-cd: cmd 0x1b timed out
Jul 22 18:40:35 localhost kernel: [80136.635692] hda: irq timeout: status=0xd0 { Busy }
Jul 22 18:40:35 localhost kernel: [80136.635694] ide: failed opcode was: unknown
Jul 22 18:40:53 localhost kernel: [80144.996951] hda: ATAPI reset complete
Jul 22 18:47:23 localhost kernel: [80335.632351] ide-cd: cmd 0x1b timed out
Jul 22 18:47:23 localhost kernel: [80335.632355] hda: irq timeout: status=0xd0 { Busy }
Jul 22 18:47:23 localhost kernel: [80335.632358] ide: failed opcode was: unknown
Jul 22 18:47:53 localhost kernel: [80349.265418] hda: ATAPI reset timed-out, status=0x80
Jul 22 18:47:56 localhost kernel: [80350.560185] ide0: reset: master: error (0x30?)
Jul 22 18:48:19 localhost kernel: [80361.199465] hda: tray open
Jul 22 18:48:19 localhost kernel: [80361.199468] end_request: I/O error, dev hda, sector 64
Jul 22 18:48:19 localhost kernel: [80361.199601] isofs_fill_super: bread failed, dev=hda, iso_blknum=16, block=16
```

I'm at a total loss. Anyone have any advice about how to proceed with troubleshooting this?

BTW, the drive works for reading operations: I installed Ubuntu with this drive, and can read DVDs and CDs okay...I haven't tried writing a CD yet.

---

### Post by JoWilly on 2006-07-22
Have you tried nerolinux ? This is the best burner on linux as it fully supports the nero 6.6.4 api.

---

### Post by professor_b on 2006-07-23
Thanks, I'll give that a shot.

---

