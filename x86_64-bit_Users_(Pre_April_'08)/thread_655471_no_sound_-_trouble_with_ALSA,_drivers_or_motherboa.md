---
title: "no sound - trouble with ALSA, drivers or motherboard?"
date: 2008-01-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by Magzimum on 2008-01-01
Hello all,

Being well aware that this problem has been posted before, I still hope for some help from some experts. None of the many answers I found proved to be a solution.

I have no sound from my speakers.

My new computer got a new ubuntu 7.10 for the AMD 64. 
The system is:
AMD 64 x2, with a M2N-E SLI motherboard with an onboard soundcard. 

I have no sound at all. I tried an audio CD, and mp3, and the system-notifications (system > preferences > sounds).

Things I tried / did:
1. I have enabled the onboard USB soundcard in my BIOS. I doublechecked.

2. I have also read and tried the solution at the end of this thread:
[http://ubuntuforums.org/showthread.php?t=539654](http://ubuntuforums.org/showthread.php?t=539654)

3. I tried to install new drivers from the ASUS website for my motherboard. This seems to have failed, but I don't understand why. The error: "ERROR: The NVIDEA kernel module was not created." - " ERROR: Installation of the audio driver has failed.  Please see the file '/var/log/nvidia-nforce-installer.log' for details.  You may find suggestions on  fixing installation problems in the README available on the Linux driver download page at www.nvidia.com." - (but there is no README on that website, and linux drivers are unix drivers, right?)

4. One other thread suggested using OSS in stead of ALSA. I tried to follow all the steps described there, but I either failed or it just doesn't work. That's why it is also listed here (below, output of aplay -l).

5. Put an old soundcard into my new pc. But I failed to get a decent result when I looked for "drivers creative labs CT4810". - no clue whether anything in my pc or in ubuntu even realizes that the second soundcard is there. 

6. Switched the speakers for a second set of speakers to rule out any chance that the speakers are broken.

In a console: 
typing "aplay -l"

********************   WARNING   *******************************
Warning! aplay uses ALSA emulation instead of the native OSS API
****************************************************************

**** List of PLAYBACK Hardware Devices ****
card 3: snd_ctl_card_info_get_id [USB sound device], device 0: OSS ID [USB sound device play]
  Subdevices: 1/1
  Subdevice #0: OSS subname
card 4: snd_ctl_card_info_get_id [USB sound device], device 1: OSS ID [USB sound device rec]
  Subdevices: 1/1
  Subdevice #0: OSS subname



then, typing "lspci":
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f1)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f3)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)
01:06.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8500 GT (rev a1)

And when I open the volume control (little icon, top right corner) I get: "No volume control GStreamer plugins and/or devices found.".

Can anyone give me some tips? I have spent an entire afternoon trying to fix this single problem, but I am no expert (far from)... Am I right to guess that I need new drivers for my soundcard?

---

### Post by Magzimum on 2008-01-08
Well, my on board sound card still doesn't work... but I've put an old soundcard in my pc, and now I get sound... everything seems normal. :)
Perhaps my motherboard/soundcard is just too new? It's ASUS/nvidea stuff, so I am assuming that its drivers are not open source, and that is part of the problem?

Although it's not urgent anymore, I'd still like to know what the actual problem is, because I don't understand.

---

### Post by Yellow Pasque on 2008-01-08
I think ASUS uses ADI chips instead of the much more common Realtek audio chips. I've seen more than a few reports of people with recent ASUS mobos having no sound.

---

### Post by arman.haghi on 2008-02-09
One *Possible* Solution:

I have the same hardware (Abit Mobo with CK804 / AC'97 audio) and had the same problem; After ensuring Kubuntu was [_[COLOR="Blue"]recognising my hardware[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=205449") etc I kept searching for 'software' answers, but it turned out to be a hardware issue all along.

I was modding my box and had removed the front panel audio connections from my mobo. Having no connectors, I've learnt, disables the back panel audio unless you use jumpers across 5/6 and 9/10. Also, ensure that onboard sound is enabled (or auto) in your BIOS menu.

i.e.

If pins are

[FONT="Courier New"]: : : ' :[/FONT]

aka

[FONT="Courier New"]2  4  6  8  10
1  3  5     9 [/FONT]

then jumpers should be placed across 5/6 and 9/10

so

[FONT="Courier New"]: : | ' |[/FONT]

aka

[FONT="Courier New"]2  4  |  8  |
1  3  |     |[/FONT]


Hope this helps,

Arman.

NOTE: Check your motherboard manual first, hardware may vary.

My manual (ala example above) was at
[http://file.abit.com.tw/pub/download/manual/english/kn8-sli.zip]("http://file.abit.com.tw/pub/download/manual/english/kn8-sli.zip")

Solution Source
[http://forums.fedoraforum.org/showthread.php?t=171686]("http://forums.fedoraforum.org/showthread.php?t=171686")

---

