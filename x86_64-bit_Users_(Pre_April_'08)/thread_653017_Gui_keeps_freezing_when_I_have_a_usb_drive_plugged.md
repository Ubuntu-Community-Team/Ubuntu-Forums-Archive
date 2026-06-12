---
title: "Gui keeps freezing when I have a usb drive plugged in."
date: 2007-12-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by noxidog on 2007-12-29
I have 64-bit Gutsy Gibbon (7.10) with Gnome.  Outside the normal quirks like getting java installed for Firefox because it's 64 bit, everything seems to be OK.  The problems are really around a 500 GB Seagate USB(one NTFS partition) disk I have.  The issues are the following:
1.  If I plug in the disk while the OS is booted, the disk does not get automounted, and of course no icon appears on my desktop.
2.  If I boot with the disk already plugged in, an Icon for the disk appears, however when I navigate to it (click it) I see the root of the drive, but if I try to go into any of the directories, the gnome file browser just freezes.  Also, I cannot pop up any other file browser after this freeze happens.

I have looked for similar problems but have been unable to find what I'm looking for.  Here is what dmesg gives:

[  103.679256] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  103.679262] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  103.679265] Info fld=0x90
[  103.679266] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
[  103.679270] end_request: I/O error, dev sr0, sector 576
[  103.679274] Buffer I/O error on device sr0, logical block 144
[  103.679277] Buffer I/O error on device sr0, logical block 145
[  103.679280] Buffer I/O error on device sr0, logical block 146
[  103.679282] Buffer I/O error on device sr0, logical block 147
[  103.679285] Buffer I/O error on device sr0, logical block 148
[  103.679287] Buffer I/O error on device sr0, logical block 149
[  103.679290] Buffer I/O error on device sr0, logical block 150
[  103.679292] Buffer I/O error on device sr0, logical block 151
[  103.679295] Buffer I/O error on device sr0, logical block 152
[  103.679298] Buffer I/O error on device sr0, logical block 153
[  149.361586] usb 6-3.3: reset full speed USB device using ehci_hcd and address 7

Thanks,

Tervel

---

### Post by smbm on 2007-12-29
Does it freeze permanently? 

I had a problem with this a while ago but it sorted itself out.

When mine froze though it was for about a minute then normal service was resumed.

---

### Post by Kilz on 2007-12-29
> **noxidog said:**
> I have 64-bit Gutsy Gibbon (7.10) with Gnome.  Outside the normal quirks like getting java installed for Firefox because it's 64 bit, everything seems to be OK.  The problems are really around a 500 GB Seagate USB(one NTFS partition) disk I have.  The issues are the following:
1.  If I plug in the disk while the OS is booted, the disk does not get automounted, and of course no icon appears on my desktop.
2.  If I boot with the disk already plugged in, an Icon for the disk appears, however when I navigate to it (click it) I see the root of the drive, but if I try to go into any of the directories, the gnome file browser just freezes.  Also, I cannot pop up any other file browser after this freeze happens.

I have looked for similar problems but have been unable to find what I'm looking for.  Here is what dmesg gives:

[  103.679256] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  103.679262] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  103.679265] Info fld=0x90
[  103.679266] sr 2:0:0:0: [sr0] Add. Sense: Unrecovered read error
[  103.679270] end_request: I/O error, dev sr0, sector 576
[  103.679274] Buffer I/O error on device sr0, logical block 144
[  103.679277] Buffer I/O error on device sr0, logical block 145
[  103.679280] Buffer I/O error on device sr0, logical block 146
[  103.679282] Buffer I/O error on device sr0, logical block 147
[  103.679285] Buffer I/O error on device sr0, logical block 148
[  103.679287] Buffer I/O error on device sr0, logical block 149
[  103.679290] Buffer I/O error on device sr0, logical block 150
[  103.679292] Buffer I/O error on device sr0, logical block 151
[  103.679295] Buffer I/O error on device sr0, logical block 152
[  103.679298] Buffer I/O error on device sr0, logical block 153
[  149.361586] usb 6-3.3: reset full speed USB device using ehci_hcd and address 7

Thanks,

Tervel

[Read this.]("http://www.engadget.com/2007/12/07/seagate-freeagent-drives-not-down-with-linux/")

---

### Post by noxidog on 2007-12-30
Thanks Kilz,

I read the link and got things to work with the following set of incantations:
sudo sdparm --command=start /dev/sdX
sudo sdparm --clear STANDBY -6 /dev/sdX
sudo sdparm -a /dev/sdX

sdX - being the usb device in question.

By the way the issue isn't isolated to Seagate.  I put another Maxtor drive and the same exact symptoms recurred.  It sounds like the driver isn't handling the narcoleptic propensities of the larger disks.  At least that's my hypothesis.

Thanks to all for your help.

Tervel

---

