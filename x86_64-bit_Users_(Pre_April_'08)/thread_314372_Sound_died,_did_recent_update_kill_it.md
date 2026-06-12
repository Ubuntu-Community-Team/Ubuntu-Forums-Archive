---
title: "Sound died, did recent update kill it?"
date: 2006-12-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by Relain on 2006-12-07
Hi, 
I have an audigy 4 in the back of my computer and it's worked since i installed ALSA .11. However all sound output has stopped as of yesterday, although lspci lsmod etc still show that it's there and i still have a volume control etc. I checked the button settings in alsamixer too, there's a certain combination that allows for analogue output. I wrote it down when i installed the card for the first time and it's still set. 

Changes i made to my computer yesterday:
1) Installed a Microsoft USB wireless desktop, this entailed a lot of fiddling with xorg.conf but that seems to have been sorted. 

2) I installed the updates suggested by the update manager, i don't actually remember what they were. Perhaps apt-cache would tell me but i don't know how to get it out.

That's it. Since then no sound at all. Has anyone else had the same problem? I tried to get the newest ALSA driver (.13) to compiler, but it had a lot of problems with the kernel source, in that it couldn't find the bits it wanted. I used synaptic to install the kernel headers and source for the 'generic' [hmm] kernel that i have. I could run ./configure with a path that points to where the files were and it went fine, but make failed.

Anyone else had the same problems ?

uname -a
```
Linux Raskolnikov 2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64 GNU/Linux

```

lspci (cropped a little)
```

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
02:00.0 Ethernet controller: Intel Corporation 82573E Gigabit Ethernet Controller (Copper) (rev 03)
02:00.3 Serial controller: Intel Corporation Intel(R) Active Management Technology - SOL (rev 03)
02:00.4 Class 0c07: Intel Corporation 82573E KCS (rev 03)
05:01.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value

```

and finally
```

[Raskolnikov:Desktop]:asoundconf list
Names of available sound cards:
Audigy2

```

Thanks for any suggestions

---

### Post by pvossen on 2006-12-07
I recently updated with Edgy and everything was working perfect.
Even my multimedia players that weren't working were after 
the upgrade. Then, a few days later I updated through the
update manager like yourself, I lost my sound just like
you. I don't know what happened, and can't seem to get things
working again. I'll let you know if I find anything that works.
I'm using the same sound card as well.


Patrick






> **Relain said:**
> Hi, 
I have an audigy 4 in the back of my computer and it's worked since i installed ALSA .11. However all sound output has stopped as of yesterday, although lspci lsmod etc still show that it's there and i still have a volume control etc. I checked the button settings in alsamixer too, there's a certain combination that allows for analogue output. I wrote it down when i installed the card for the first time and it's still set. 

Changes i made to my computer yesterday:
1) Installed a Microsoft USB wireless desktop, this entailed a lot of fiddling with xorg.conf but that seems to have been sorted. 

2) I installed the updates suggested by the update manager, i don't actually remember what they were. Perhaps apt-cache would tell me but i don't know how to get it out.

That's it. Since then no sound at all. Has anyone else had the same problem? I tried to get the newest ALSA driver (.13) to compiler, but it had a lot of problems with the kernel source, in that it couldn't find the bits it wanted. I used synaptic to install the kernel headers and source for the 'generic' [hmm] kernel that i have. I could run ./configure with a path that points to where the files were and it went fine, but make failed.

Anyone else had the same problems ?

uname -a
```
Linux Raskolnikov 2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64 GNU/Linux

```

lspci (cropped a little)
```

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
02:00.0 Ethernet controller: Intel Corporation 82573E Gigabit Ethernet Controller (Copper) (rev 03)
02:00.3 Serial controller: Intel Corporation Intel(R) Active Management Technology - SOL (rev 03)
02:00.4 Class 0c07: Intel Corporation 82573E KCS (rev 03)
05:01.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value

```

and finally
```

[Raskolnikov:Desktop]:asoundconf list
Names of available sound cards:
Audigy2

```

Thanks for any suggestions

---

### Post by drphilngood on 2006-12-07
Try troubleshooting with this:

[Comprehensive Sound Problem Solutions Guide]("http://www.ubuntuforums.org/showthread.php?t=205449")

and post back if you still need help.  The ALSA settings are usually the culprit and adjusting the volume or unmuting one or more of them is usually the cure.

---

