---
title: "Sound on MSI K8N Neo 4 Platinum SLI?"
date: 2005-07-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by kurtwisener on 2005-07-18
I have recently reinstalled Ubuntu after a firey affair with Gentoo and FreeBSD.  I thought I had the sound issue whipped after I read and followed the advice posted [here](http://www.ubuntuforums.org/showthread.php?t=21211).  Now I still have no sound and dmesg gives me the following:
```
ALSA /usr/src/alsa-driver-1.0.8/alsa-kernel/pci/ac97/ac97_codec.c:1907: AC'97 0 does not respond - RESET
ALSA /usr/src/alsa-driver-1.0.8/alsa-kernel/pci/ac97/ac97_codec.c:1916: AC'97 0 access is not valid [0x0], removing mixer.
CA0106: probe of 0000:01:0d.0 failed with error -5
``` 

This is becoming painful.  

As a side note, I also followed the instructions [here](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+7.1.&chip=SB0410%2C+P17&module=ca0106) 
at ALSA.

Any help would be so appreciated.
Thank you.

 ](*,)

---

### Post by Jet2k5 on 2005-07-18
I was going to get this board.  But some quick google searches will tell you that the mobo isnt really that greatly supported in Linux.  Not just the SLI but just MSI K8N Neo 4 versions.  Wish I could help, I'm just throwing in my 2 cents about the mobo.

---

### Post by Steve1961 on 2005-08-15
I've got the non-SLI MSI K8 Neo4 Platinum.  This how to fixed my sound problem:

[http://ubuntuforums.org/showthread.php?t=19089&highlight=change+sound+daemon](http://ubuntuforums.org/showthread.php?t=19089&highlight=change+sound+daemon)

---

### Post by D@ffy on 2005-08-24
[QUOTE=Steve1961]I've got the non-SLI MSI K8 Neo4 Platinum.  This how to fixed my sound problem:

[http://ubuntuforums.org/showthread.php?t=19089&highlight=change+sound+daemon](http://ubuntuforums.org/showthread.php?t=19089&highlight=change+sound+daemon)[/QUOTE]
Doesn't work here. Always get an error that building the testing pipeline has failed, with ALSA, OSS, and ESD, all the same. When I start Totem media player I get an error that ALSA devide default doesn't exist.  :???: 
When I run alsamixer I get: function snd_ctl_open failed for default: No such file or directory

This is what I get with lsmod | grep snd:
> snd_ca0106             30532  0
snd_ac97_codec         80720  1 snd_ca0106
snd_pcm_oss            63392  0
snd_mixer_oss          20864  1 snd_pcm_oss
snd_pcm               102796  3 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_timer              26376  1 snd_pcm
snd                    66056  6 snd_ca0106,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11168  1 snd
snd_page_alloc         11400  2 snd_ca0106,snd_pcm


Any suggestions? I tried a lot of topics on this forum but nothing seems to help.

For all clarity: I'm running Ubuntu 5.04 AMD64 on a K8N SLI motherboard with SB Live! 24 on-board sound.

---

### Post by Corbelius on 2005-08-25
Try to install nforce driver for linux: [http://www.nvidia.com/object/linux_nforce_amd64_1.0-0306](http://www.nvidia.com/object/linux_nforce_amd64_1.0-0306)

---

### Post by DancingSun on 2005-08-25
Hey Corbelius,
I like that avatar :D

---

### Post by DancingSun on 2005-08-25
[QUOTE=Corbelius]Try to install nforce driver for linux: [http://www.nvidia.com/object/linux_nforce_amd64_1.0-0306](http://www.nvidia.com/object/linux_nforce_amd64_1.0-0306)[/QUOTE]
I heard the nForce drivers doesn't work with S/PDIF, is that true?

Edit:
I just checked those nForce drivers, they dont' seem to support nForce4.

---

### Post by Corbelius on 2005-08-25
[QUOTE=DancingSun]Hey Corbelius,
I like that avatar :D[/QUOTE]

eh eh :D

[QUOTE=DancingSun]I heard the nForce drivers doesn't work with S/PDIF, is that true?

Edit:
I just checked those nForce drivers, they dont' seem to support nForce4.[/QUOTE]

Where you have read this?

---

### Post by DancingSun on 2005-08-25
[QUOTE=Corbelius](...)
Where you have read this?[/QUOTE]
The S/PDIF part, I read in some Linux forums.  I did a search on "nForce 4 S/PDIF", or soemthing like that, in Yahoo.

The no support for nForce4 part, I read in the release notes of the drivers page that you linked.  It doesn't explicitly state that nForce4 is unsupported, but it does state which revision that nForce3 support was added, but had no mention of nForce4 at all.  Granted nForce3 and 4 are very similar (basically only socket 939, SATA, hardware firewall, and gigabit ethernet are added in nForce4, correct?), there still a risk that things can go very wrong as these are chipset drivers.  And of course, being a Linux newbie makes the risk higher as well, since I won't know how to restore the system...besides a reinstall.

Hmm...actually in the release notes, I just saw AC3 pass-through is added 4 releases ago.

---

### Post by D@ffy on 2005-08-25
[QUOTE=Corbelius]Try to install nforce driver for linux: [http://www.nvidia.com/object/linux_nforce_amd64_1.0-0306](http://www.nvidia.com/object/linux_nforce_amd64_1.0-0306)[/QUOTE]
Already tried that the previous time I installed Ubuntu, but that driver only works for the standard Ac97 I think. Anyway, it didn't work. (and it only contains network and audio driver)

---

### Post by DancingSun on 2005-08-25
[QUOTE=D@ffy]Already tried that the previous time I installed Ubuntu, but that driver only works for the standard Ac97 I think. Anyway, it didn't work. (and it only contains network and audio driver)[/QUOTE]
Oh yeah, I think that motherboard uses an integrated Soundblaster Live! 24-bit chip.  I heard those sound chips are a pain in the ass on Linux....you might want to search on how to get soundblaster soundcards working and use that as a reference.

---

### Post by front243 on 2005-08-27
[QUOTE=Steve1961]I've got the non-SLI MSI K8 Neo4 Platinum.  This how to fixed my sound problem:

[http://ubuntuforums.org/showthread.php?t=19089&highlight=change+sound+daemon](http://ubuntuforums.org/showthread.php?t=19089&highlight=change+sound+daemon)[/QUOTE]

I have the same problem with same motherboard.

I am a bit stuck in that guide, it says I have to "right click the volume control on the panel", but I have no volume control, and if I try to add it nothing seems to happen!

Any advice?

Edit: By the way, I got sound working fine on Fedora Core 4, so I know it definately should work on Linux. But now that I am testing Ubuntu and like it better I would rather have sound in Ubuntu than reinstall FC4.

---

### Post by DancingSun on 2005-08-31
[QUOTE=front243]I have the same problem with same motherboard.

I am a bit stuck in that guide, it says I have to "right click the volume control on the panel", but I have no volume control, and if I try to add it nothing seems to happen!

Any advice?

Edit: By the way, I got sound working fine on Fedora Core 4, so I know it definately should work on Linux. But now that I am testing Ubuntu and like it better I would rather have sound in Ubuntu than reinstall FC4.[/QUOTE]
I think you can add it by right clicking on the GNOME panel and choose "Add to Panel...", you should see "Volume Control" on the list.

---

