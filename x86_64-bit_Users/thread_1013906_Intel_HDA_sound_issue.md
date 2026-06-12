---
title: "Intel HDA sound issue"
date: 2008-12-17
forum: x86 64-bit Users
---

### Post by Firebat451 on 2008-12-17
I recently installed Ubuntu 8.10 64bit on my Sony Vaio desktop and the sound didn't work. After playing with things a bit I found that the center channel (the yellow jack) worked, but very softly. The rest of the jacks including mic and audio in seem to not work. Here's some info:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
Subsystem: Sony Corporation Device 81e7
Flags: bus master, fast devsel, latency 0, IRQ 22
Memory at 902c0000 (64-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel

I've already tried a number of how-to guides and have had no success.

It's an on board if something up there didn't tell you that already. If there's anything else you need to know just ask, any help is welcome. Thanks.

---

### Post by dabl on 2008-12-17
Check this:

[http://ubuntuforums.org/showthread.php?t=983987&highlight=audio+sony+vaio](http://ubuntuforums.org/showthread.php?t=983987&highlight=audio+sony+vaio)

---

### Post by Firebat451 on 2008-12-17
I thought of the external amplifier option.  Every time I've installed Ubuntu 8.04 and earlier on any machine I had to go to the alsamixer and disable the external amp.  However, I can't seem to find that option anywhere in 8.10.  All I have in the alsa mixer is "master" and "captur".  Both are set to 100% and are not muted.  Same for volume controls; all I have in the preferences are playback and recording for all device options.

---

### Post by marttali on 2008-12-18
try to update your motherboard bios first, made all the difference for me ( it was not laptop though) It's rather common cause.

---

### Post by Firebat451 on 2008-12-20
I just checked, I have the latest bios version already.  Good idea though; I hadn't thought of it.

---

