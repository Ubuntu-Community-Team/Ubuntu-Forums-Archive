---
title: "yaboot disappears"
date: 2005-12-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by burobaaje on 2005-12-27
I have OSX 10.3.9 and ubunto on the internal drive of an iMac.  I have an external firewire drive with OSX 10.4.3.

After booting OSX from the firewire drive, I cannot get back to ubuntu.  No matter how I start the computer, it automatically boots into OSX on the internal drive instead of giving me a choice.

Does 10.4.3 overwrite yaboot making the mac only boot into OSX?

Anyone know how to restore yaboot and ubuntu without re-intalling?  This has happened before and I blamed it on something else, but now know that after booting the firewire drive, yaboot is gone!

---

### Post by linear on 2005-12-27
See this item in the wiki:

[https://wiki.ubuntu.com/YabootConfigurationForMacintoshPowerPCsDualBoot](https://wiki.ubuntu.com/YabootConfigurationForMacintoshPowerPCsDualBoot)

(Scroll down to "You lost the yaboot menu! Now what?")

---

### Post by burobaaje on 2005-12-27
[QUOTE=linear]See this item in the wiki:

[https://wiki.ubuntu.com/YabootConfigurationForMacintoshPowerPCsDualBoot](https://wiki.ubuntu.com/YabootConfigurationForMacintoshPowerPCsDualBoot)

(Scroll down to "You lost the yaboot menu! Now what?")[/QUOTE]

Thanks.

Unfortunately I used iPartition to make room for ubuntu and therefore yaboot is not the first bootable partition so re-setting the PRAM did not work, but I had already figured out a way to get into ubuntu by:

Hold down command, option, o, f, keys while starting the mac to get into OpenFirmware with prompt 0>

Type:
0>boot hd:XX,yaboot

where XX is the number of the yaboot partition.

This loads yaboot and gets into ubuntu.  I will fix it to work auto later.

---

### Post by MonolithTMA on 2005-12-28
I think changing your Startup Disk in OS X is what writes over Yaboot. I could be wrong, but the two times I've had issues with Yaboot I had just changed Startup Disks.

---

### Post by burobaaje on 2005-12-28
[QUOTE=MonolithTMA]I think changing your Startup Disk in OS X is what writes over Yaboot. I could be wrong, but the two times I've had issues with Yaboot I had just changed Startup Disks.[/QUOTE]

Same here.  No doubt it is changing startup disk in OS X.  I previously blamed Ext2FS, but now know it was _not_ the culprit!

---

