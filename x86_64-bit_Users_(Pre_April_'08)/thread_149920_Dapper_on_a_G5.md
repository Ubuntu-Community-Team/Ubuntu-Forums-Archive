---
title: "Dapper on a G5"
date: 2006-03-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by aimislame15 on 2006-03-24
<soapbox> The darn fans run at full blast all the time on my Dual 2.3ghz G5 1gb ram </soapbox>

I truly hate it. I checked out my System Monitor and I am not using more than 3% of processor speed when this happens. I want to resolve this issue asap so I'm downloading a newer Dapper release in hopes that it works.

---

### Post by dermotti on 2006-03-24
Any bios options to disbale that feature?

---

### Post by aimislame15 on 2006-03-24
Errr... I dont know

---

### Post by jdp on 2006-03-24
There is no BIOS on a Mac.  The fans are under OS control, and it seems no one has been able to create software to control them properly just yet.  Such is life trying to develop software without manufacturers providing detailed docs.  It's the same situation for the Airport Extreme.

Sorry.  It' be a lot easier if Apple shared some design secrets, but alas.

---

### Post by aimislame15 on 2006-03-24
In Yellow Dog Linux 4.0 they had fan control. In Ubuntu Breezy, I had fan control. In dapper, bleh. 

Besides, I've got my Airport Extreme working too on my iBook :P

---

### Post by ssam on 2006-03-25
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/35036](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/35036)

click on the unconfirmed and set it to confirmed. and add a comment that you are also experiencing the problem, and what model G5 you have. you should also say that it is a regression from breezy.

---

### Post by stmiller on 2006-03-25
I have a dual G5 2x2Ghz CPUs, PCIX model. Fans are under control here.

Output of dmesg:

```
[   25.608373] io scheduler cfq registered
[   25.609377] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   25.609555] MacIO PCI driver attached to K2 chipset
[   25.610313] PowerMac G5 Thermal control driver 1.2b2
[   25.610466] Detected fan controls:
[   25.610470]   0: PWM fan, id 1, location: BACKSIDE,SYS CTRLR FAN
[   25.610473]   1: RPM fan, id 2, location: DRIVE BAY
[   25.610476]   2: PWM fan, id 2, location: SLOT,PCI FAN
[   25.610479]   3: RPM fan, id 3, location: CPU A INTAKE
[   25.610481]   4: RPM fan, id 4, location: CPU A EXHAUST
[   25.610484]   5: RPM fan, id 5, location: CPU B INTAKE
[   25.610493]   6: RPM fan, id 6, location: CPU B EXHAUST
[   25.610554] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   25.610563] ide: Assuming 33MHz system bus speed for PIO modes; overr
```

Is your G5 one of the newer G5s (Nov/Dec 2005?)

---

### Post by tidris on 2006-03-25
Just for the record, the fans run at normal speed (as in OSX) on my Dual 2GHz G5 with Dapper Flight 5. On the other hand, the F12 key doesn't emulate the right mouse button, and that is a major irritation.

---

### Post by aimislame15 on 2006-03-25
To tell you the truth, I can't remember exactly when I got my G5, but I'm pretty sure it was pre-November. My install CD was from March 20, but I'll try a newer CD. I Hope it works.

---

### Post by aimislame15 on 2006-03-25
The thing that I find weird is that the fans don't spin up until I actually do something in GNOME (IE: open an app etc.).... Pisses me off having to listen to the fans. Is it even safe to run it like this for  long without risk of burning out the fan motor?

---

