---
title: "30 Second Freezes with ata vomit."
date: 2008-07-17
forum: x86 64-bit Users
---

### Post by LibertyShadow on 2008-07-17
Sometimes when I log in or when I suspend/resume, my computer freezes for 30 seconds or more.  My logs are full of ata error messages, like below:

> 
Jul 17 11:02:04 Shadowcat-XPS kernel: [ 1282.238227] ACPI: PCI interrupt for device 0000:0c:00.0 disabled
Jul 17 11:02:33 Shadowcat-XPS kernel: [ 1284.787533] ata1.00: exception Emask 0x0 SAct 0x3f SErr 0x0 action 0x2 frozen
Jul 17 11:02:33 Shadowcat-XPS kernel: [ 1284.787644] ata1.00: cmd 61/08:00:9a:f1:29/00:00:09:00:00/40 tag 0 ncq 4096 out
Jul 17 11:02:33 Shadowcat-XPS kernel: [ 1284.787647]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
Jul 17 11:02:33 Shadowcat-XPS kernel: [ 1284.787752] ata1.00: status: { DRDY }
Jul 17 11:02:33 Shadowcat-XPS kernel: [ 1284.787842] ata1.00: cmd 61/08:08:7a:dc:b1/00:00:05:00:00/40 tag 1 ncq 4096 out
Jul 17 11:02:33 Shadowcat-XPS kernel: [ 1284.787844]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jul 17 11:02:33 Shadowcat-XPS kernel: [ 1284.787939] ata1.00: status: { DRDY }
Jul 17 11:02:33 Shadowcat-XPS kernel: [ 1284.788028] ata1.00: cmd 61/08:10:62:0b:1e/00:00:09:00:00/40 tag 2 ncq 4096 out
Jul 17 11:02:33 Shadowcat-XPS kernel: [ 1284.788031]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jul 17 11:02:33 Shadowcat-XPS kernel: [ 1284.788126] ata1.00: status: { DRDY }
Jul 17 11:02:33 Shadowcat-XPS kernel: [ 1284.788215] ata1.00: cmd 61/08:18:f2:4d:1b/00:00:09:00:00/40 tag 3 ncq 4096 out
Jul 17 11:02:33 Shadowcat-XPS kernel: [ 1284.788217]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jul 17 11:02:33 Shadowcat-XPS kernel: [ 1284.788313] ata1.00: status: { DRDY }
Jul 17 11:02:33 Shadowcat-XPS kernel: [ 1284.788407] ata1.00: cmd 61/08:20:32:4e:1b/00:00:09:00:00/40 tag 4 ncq 4096 out
Jul 17 11:02:33 Shadowcat-XPS kernel: [ 1284.788410]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jul 17 11:02:33 Shadowcat-XPS kernel: [ 1284.788504] ata1.00: status: { DRDY }
Jul 17 11:02:33 Shadowcat-XPS kernel: [ 1284.788598] ata1.00: cmd 61/08:28:fa:af:1b/00:00:09:00:00/40 tag 5 ncq 4096 out
Jul 17 11:02:33 Shadowcat-XPS kernel: [ 1284.788600]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jul 17 11:02:33 Shadowcat-XPS kernel: [ 1284.788696] ata1.00: status: { DRDY }
Jul 17 11:02:33 Shadowcat-XPS kernel: [ 1284.842138] ata1: soft resetting link
Jul 17 11:02:33 Shadowcat-XPS kernel: [ 1284.846200] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 17 11:02:33 Shadowcat-XPS kernel: [ 1284.851104] ata1.00: configured for UDMA/133
Jul 17 11:02:33 Shadowcat-XPS kernel: [ 1284.851144] ata1: EH complete

> 
Jul 17 11:13:29 Shadowcat-XPS kernel: [    2.091094] PM: Finishing wakeup.
Jul 17 11:13:29 Shadowcat-XPS kernel: [    2.091097] Restarting tasks ... done.
Jul 17 11:13:59 Shadowcat-XPS kernel: [   32.159413] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x2 frozen
Jul 17 11:13:59 Shadowcat-XPS kernel: [   32.159515] ata1.00: cmd 60/40:00:ea:25:43/00:00:06:00:00/40 tag 0 ncq 32768 in
Jul 17 11:13:59 Shadowcat-XPS kernel: [   32.159517]          res 40/00:fe:00:00:00/00:00:00:00:00/40 Emask 0x4 (timeout)
Jul 17 11:13:59 Shadowcat-XPS kernel: [   32.159617] ata1.00: status: { DRDY }
Jul 17 11:14:00 Shadowcat-XPS kernel: [   32.470847] ata1: soft resetting link
Jul 17 11:14:00 Shadowcat-XPS kernel: [   32.476557] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 17 11:14:00 Shadowcat-XPS kernel: [   32.489360] ata1.00: configured for UDMA/133
Jul 17 11:14:00 Shadowcat-XPS kernel: [   32.489373] ata1: EH complete
Jul 17 11:14:00 Shadowcat-XPS kernel: [   32.507267] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Jul 17 11:14:00 Shadowcat-XPS kernel: [   32.571078] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 11:14:00 Shadowcat-XPS kernel: [   32.571081] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul 17 11:14:00 Shadowcat-XPS kernel: [   32.571383] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 11:14:30 Shadowcat-XPS kernel: [   34.982344] ata1.00: cmd 61/08:18:e2:41:a3/00:00:05:00:00/40 tag 3 ncq 4096 out
Jul 17 11:14:30 Shadowcat-XPS kernel: [   34.982346]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
Jul 17 11:14:30 Shadowcat-XPS kernel: [   34.982478] ata1.00: status: { DRDY }
Jul 17 11:14:30 Shadowcat-XPS kernel: [   35.023807] ata1: soft resetting link
Jul 17 11:14:30 Shadowcat-XPS kernel: [   35.029882] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jul 17 11:14:30 Shadowcat-XPS kernel: [   35.034453] ata1.00: configured for UDMA/133
Jul 17 11:14:30 Shadowcat-XPS kernel: [   35.034494] ata1: EH complete
Jul 17 11:14:30 Shadowcat-XPS kernel: [   35.036422] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
Jul 17 11:14:31 Shadowcat-XPS kernel: [   35.041206] sd 0:0:0:0: [sda] Write Protect is off
Jul 17 11:14:31 Shadowcat-XPS kernel: [   35.041219] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Jul 17 11:14:31 Shadowcat-XPS kernel: [   35.054644] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jul 17 11:14:31 Shadowcat-XPS kernel: [   35.673724] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
Jul 17 11:14:31 Shadowcat-XPS kernel: [   35.673728] iwl4965: Copyright(c) 2003-2007 Intel Corporation
Jul 17 11:14:31 Shadowcat-XPS kernel: [   35.673887] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Jul 17 11:14:31 Shadowcat-XPS kernel: [   35.673926] PCI: Setting latency timer of device 0000:0c:00.0 to 64
Jul 17 11:14:31 Shadowcat-XPS kernel: [   35.674657] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
Jul 17 11:14:31 Shadowcat-XPS kernel: [   35.728643] tg3.c:v3.86 (November 9, 2007)


This problem started shortly after I reinstalled last week.  Should I reinstall again?  I have googled this problem, and found many results. This seems to be the closest:[ https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217920]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217920")  The bug looks inactive though...

I am running Hardy Herron 8.04.1 x64.

---

### Post by LibertyShadow on 2008-07-18
I can't take this. It happened when I went to suspend.  When I just tried to resume It happened twice in a row, then I finally got to the lock screen and Authentication Failed twice in a row.  I tried to get to a tty but my computer froze and I powered it off.  

I'm going to reinstall and see if this happens on a fresh install.  Otherwise it is a configuration error.

---

