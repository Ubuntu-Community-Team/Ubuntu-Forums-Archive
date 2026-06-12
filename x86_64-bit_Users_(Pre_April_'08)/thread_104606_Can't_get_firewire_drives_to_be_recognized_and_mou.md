---
title: "Can't get firewire drives to be recognized and mount"
date: 2005-12-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by rfrost on 2005-12-16
Very odd. I'm on the latest kubuntu PPC distro and I did the default install. [BTW, on my rev 2 G3 B+W, &00+MB memory--and no, this isn't the B+W model with the flaky firewire) None of my drives, even the ATAs, mounted initially, but at least with the ATAs they were recognized and I edited the fstab and now they are up.

It seems that the FW drives are simply not recognized at all, so of course, they cannot be mounted.

What am I missing here?

TIA.

---

### Post by ssam on 2005-12-16
do you get anything interesting in dmseg?

(type
```
dmesg
```
at the terminal, and post the last 10 or 20 lines here is you want)

---

### Post by rfrost on 2005-12-16
Thanks. This is what I get:

[   92.940750] ieee1394: Node added: ID:BUS[0-00:1023]  GUID[0030e001e00085a7]
[   92.957068] ieee1394: Node added: ID:BUS[0-01:1023]  GUID[00d04b4113092783]
[   92.962940] ieee1394: Host added: ID:BUS[0-02:1023]  GUID[0800070200000000]
[   94.462551] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[   94.505589] scsi2 : SCSI emulation for IEEE-1394 SBP-2 Devices
[   97.668803] ts: Compaq touchscreen protocol output
[  100.460142] phy registers:
[  100.460156]  1400 782d 7810 0003 00a1 45e1 0001 0000
[  100.470832]  0000 0000 0000 0000 0000 0000 0000 0000
[  100.481502]  0000 0000 4000 0000 2ffb 0010 0000 0002
[  100.492173]  0001 0000 0000 0000 0000 0000 0000 0000
[  100.610087] NET: Registered protocol family 17
[  106.584903] NET: Registered protocol family 10
[  106.585361] Disabled Privacy Extensions on device c026ad58(lo)
[  106.585856] IPv6 over IPv4 tunneling driver
[  116.078985] ieee1394: sbp2: Error logging into SBP-2 device - login timed-out
[  116.084496] sbp2: probe of 0030e001e00085a7-0 failed with error -16
[  116.084642] scsi3 : SCSI emulation for IEEE-1394 SBP-2 Devices
[  116.599410] Bluetooth: Core ver 2.7
[  116.599444] NET: Registered protocol family 31
[  116.599452] Bluetooth: HCI device and connection manager initialized
[  116.599491] Bluetooth: HCI socket layer initialized
[  116.705507] Bluetooth: L2CAP ver 2.7
[  116.705526] Bluetooth: L2CAP socket layer initialized
[  116.790790] Bluetooth: RFCOMM ver 1.5
[  116.790827] Bluetooth: RFCOMM socket layer initialized
[  116.790866] Bluetooth: RFCOMM TTY layer initialized
[  117.070934] eth0: no IPv6 routers present
[  120.486257] Linux agpgart interface v0.101 (c) Dave Jones
[  120.519881] [drm] Initialized drm 1.0.0 20040925
[  120.566058] [drm] Initialized r128 2.5.0 20030725 on minor 0: ATI Technologie                                    s Inc Rage 128 RE/SG
[  137.704218] ieee1394: sbp2: Error logging into SBP-2 device - login timed-out
[  137.709935] sbp2: probe of 00d04b4113092783-0 failed with error -16

Seems to be a problem communicating b/w the drives and the unit.

---

### Post by ssam on 2005-12-17
sbp is a scsi tunnel through firewire ([http://www.linux1394.org/sbp2.php)](http://www.linux1394.org/sbp2.php)).

you should probably file a bug at [http://bugzilla.ubuntu.org/](http://bugzilla.ubuntu.org/) 

they'll probably ask for some more info, but might know whats wrong.

---

### Post by rfrost on 2005-12-17
Actually, the error is Apple's not ubuntu's. I had a spare PCI==>1394 card kicking around, so I installed it and whew!, easy recognition. Now all I need to do is get rid of these damn 1394==>ATA enclosures that limit drive size to 128GB.

Thanks so much for your help. On to figuring out how to get my 5-digit UID accepted into linux so that I can read/write to all my drives.

---

### Post by enupnia on 2006-01-17
I have exactly the same problem...

could you explain better how to solve it?

thanks

---

