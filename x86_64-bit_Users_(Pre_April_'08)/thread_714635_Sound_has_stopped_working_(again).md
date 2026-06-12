---
title: "Sound has stopped working (again)"
date: 2008-03-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Maelgwyn on 2008-03-04
Hi guys,

I know this topic has been beaten to death, but it's just happened to me and I can't seem to fix it!!

I've had sound issues previously, and I was prepared for it to happen again as I've re-installed Gutsy from 32-bit to 64-bit...

Sound appears to be touch & go for me - sometimes it goes but if I reboot then I seem to have a less than 50% chance of it going again when I boot!

I've gone through a few of the tutorial/fixes on the Ubuntu forums, but nothing is working for me, and my boyfriend is laughing at me for having an 'inferior' system :mad:

Please help! :confused:

---

### Post by Cappy on 2008-03-04
Do you have two sound cards? You need to provide information.

If you do have 2 sound cards try this (for instance, an onboard soundcard on the motherboard and then an Audigy or any other sound card in the PCI slots):
[http://oktyabr.wordpress.com/2007/01/18/alsa-sound-card-order/](http://oktyabr.wordpress.com/2007/01/18/alsa-sound-card-order/)
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/45786](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/45786)

---

### Post by Yellow Pasque on 2008-03-04
Can we get some info on your computer?
Run this:
```
sudo update-pciids; lspci
```

Also see if these commands return anything:
```
cat /proc/asound/card0/codec#* | grep Codec
aplay -l 
```

---

### Post by Maelgwyn on 2008-03-04
hah sorry - I forgot that bit..:

firstly:
```
100%[====================================>] 131,284       30.05K/s    ETA 00:00

22:26:59 (29.98 KB/s) - `/usr/share/misc/pci.ids.gz.new' saved [131284/131284]

Done.
00:00.0 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation MCP65 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP65 SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP65 Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP65 USB Controller (rev a3)
00:06.0 Ethernet controller: nVidia Corporation MCP65 Ethernet (rev a3)
00:07.0 Audio device: nVidia Corporation MCP65 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP65 PCI bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP65 IDE (rev a1)
00:0a.0 IDE interface: nVidia Corporation MCP65 SATA Controller (rev a3)
00:0d.0 PCI bridge: nVidia Corporation MCP65 PCI Express bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
01:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
nik@taonga:~$ 

```Secondly:
```
nik@taonga:~$ cat /proc/asound/card0/codec#0 | grep Codec
Codec: Realtek ALC888
```

And thirdly:
```
nik@taonga:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
nik@taonga:~$ 

```

---

### Post by Yellow Pasque on 2008-03-04
Try upgrading your ALSA with these scripts
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

You may also need to configure your alsa-base file
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

### Post by Maelgwyn on 2008-03-04
I've run the two .sh scripts, and now it appears that sound is working only there's no sound! I'll clarify:

When I open Sound Preferences and click on Test, the little box pops up saying "testing" with the slider but there's no sound. If I change from Autodetect to anything else it does the same, except for ESD, which throws an error:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not establish connection to sound server

---

### Post by Maelgwyn on 2008-03-04
As for the configuring the alsa-base file, I've tried adding

options snd-hda-intel model=acer

or

options snd-hda-intel model=acer-inspire

But still no sound =(

---

### Post by erginemr on 2008-03-04
OK. Try this:
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

Long story short, you need to enable backports and install linux-backports-modules-generic from Synaptic.

I know that it has helped quite a few people...

---

### Post by Maelgwyn on 2008-03-04
I thought I'd already done that, but I hadn't!!

Have installed linux-backports-modules-generic and rebooted, but still no joy >.<

---

### Post by Yellow Pasque on 2008-03-04
Have you gone into alsamixer and unmuted all the channels?

---

### Post by Maelgwyn on 2008-03-04
yep

---

### Post by erginemr on 2008-03-05
Can you please refer to the following topic:
[http://ubuntuforums.org/showthread.php?t=711622&highlight=live+alsa&page=2](http://ubuntuforums.org/showthread.php?t=711622&highlight=live+alsa&page=2)

and to my suggestion about using the Live CD to see if the sound works and to inspect/retrieve the config files if it does.

---

### Post by Maelgwyn on 2008-03-05
> **erginemr said:**
> Can you please refer to the following topic:
[http://ubuntuforums.org/showthread.php?t=711622&highlight=live+alsa&page=2](http://ubuntuforums.org/showthread.php?t=711622&highlight=live+alsa&page=2)

and to my suggestion about using the Live CD to see if the sound works and to inspect/retrieve the config files if it does.


Nope didn't work... Which is weird - because it used to! But I get the same problem. Little box pops up saying "Testing..." but no sound comes out. I've double-checked my speakers are plugged into the Line Out plug (little green one). I've also tried the Line Out port on the front-right side of my box, but no luck there either >.<

I've installed Envy and rebooted and still nothing.

/cry

---

### Post by erginemr on 2008-03-05
If the sound doesn't work even Live CD, that would only mean that something has regrettably gone awry in your hardware.

You need more witnesses(!) to your case to make sure:

1- If your computer is dual booted, any consistent sound in Windows?

2- Any other Linux Live CD you can download and try booting to hear the sound? PCLinux OS? Fedora Core?

3- Any setting in BIOS that relates to sound?

I sincerely hope that this is only a software issue. To give you an idea, here are the screenshots of a virtual Ubuntu installation where I have disabled the sound via VirtualBox settings.

---

### Post by Maelgwyn on 2008-03-05
Just to confuse matters further, I shut my computer down last night and when I booted this morning - I have sound! :guitar:

I really wish I knew what was doing this, but until then I'll just >not< turn my computer off :P

---

### Post by Yellow Pasque on 2008-03-05
You probably just needed to reboot after running the second ALSA upgrade script or configurin your als-base file. I think it will be safe to reboot in the future.

I'm glad to hear your issue is resolved. Show those Windoze users whose OS is better! :)

---

