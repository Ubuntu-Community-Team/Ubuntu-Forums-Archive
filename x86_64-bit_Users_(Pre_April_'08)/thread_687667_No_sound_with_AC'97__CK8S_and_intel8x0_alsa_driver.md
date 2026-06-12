---
title: "No sound with AC'97 / CK8S and intel8x0 alsa drivers"
date: 2008-02-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by nakerlund on 2008-02-04
The past two days, I've been trying to get my sound to work on my new ubuntu 7.10 installation without success. I installed 7.10 on my second hard drive and after some fiddeling managed to setup the dual boot. (Ubuntu thought it was on hd0 and thought so again when I updated some other thing) I got vista running on the other drive and the sound works there. (Did have some issues with vista at start but that seemed to be because of their new sound kernel)

Anyway, in Ubuntu there has not been any sound, and not from the live CD either. I've checked all the settings that I can find and the hardware(nforce3's realtek AC'97) is found and the correct driver (intel8x0) is used.

```
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800 GT] (rev a1)
02:0b.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
```

aplay -l also lists it:

```
**** List of PLAYBACK Hardware Devices ****
card 0: CK8S [NVidia CK8S], device 0: Intel ICH [NVidia CK8S]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK8S [NVidia CK8S], device 2: Intel ICH - IEC958 [NVidia CK8S - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

and asoundconf list
```
Names of available sound cards:
CK8S
```

I also made sure the correct driver(snd_intel8x0) is used on alsa's list and lshw says it is installed
```
lshw -C sound
 *-multimedia            
       description: Multimedia audio controller
       product: nForce3 250Gb AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:06.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0
```

I followed this [guide]("https://help.ubuntu.com/community/SoundTroubleshooting") but without any success.. did manage to loose gdm though...

The only two errors I get are when setting ESD in sound preferences. It says it is unable to connect to sound server. And, when trying to sound capture... actually I get a fee different errors from the different options. They all seem to say, "Failed to construct test pipeline for 'gconfaudiosrc' ! audioconvert !audioresample ! gconfaudiosink profile=chat".

I tried to follow but when trying to configure... 
```
./configure --with-cards=intel8x0m --with-sequencer=yes
``` it ends up saying, 'configure: error: cannot find install-sh or install.sh in "." "./.." "./../.."'.

And make/make install won't work after that.

I also tried getting drivers from [realtek]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false#2") but the installer failed.. saying:
```
checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
Remove Folder.....
./install: 102: alsaconf: not found
```

I tried to find the curses in synaptic but couldn't find the ones it wanted... and as far as I understand, alsaconf doesn't really do anything anymore and has been removed.

And I have checked that the sound isn't muted or turned down.. both in alsamixer and the Volume Control. I played around with the settings but never any sound. After messing around, I reset the sound settings following Sound Troubleshooting's instructions.

I also tried to run [the alsa-info script]("http://bulletproof.servebeer.com/alsa/scripts/alsa-info.sh") but there seems to be a fatal bug in it at the moment and it doesn't even get to the point where it should ask before running.

I was considering jack sensing might screw things up, so I plugged in two speakers hoping one of them would be in the right port... but no such luck.

And now I'm stumped! Does anyone have any ideas of what to try next?

---

### Post by nakerlund on 2008-02-06
In a radical attempt to get my sound working, I looked up non-debian based 32bit distributions on wikipedia running kde (Everything, I understand, Ubuntu isn't). I picked PCLinuxOS 2007 since it has LiveCD support too, but my sound didn't work in it either. :(

So, I figure it is either an alsa issue or a kernel one. Does anyone know of a good step by step guide to build a newer version of either? Or should I just wait for ubuntu updates and hope they solve my problems?

(Oh and if there is a moderator around, this probably is not the right place for this thread since this doesn't seem to be a 64 bit issue)

---

### Post by AutomaticUNC on 2008-02-09
I am having the same exact problem except I have a 32-bit system.  Have you noticed that when Ubuntu starts the startup sound plays and then you get no sound afterwards?  I am having that issue.  Sorry for no ideas on how to fix it.

---

### Post by raaki_88 on 2008-02-10
dudes 

everything is fine 

but have you installed  any of lib curses for c , rubu and python 

so 

do the following

$sudo synaptic

search for lib curses and install them 

then execute ./configure that should fixup

---

### Post by Yellow Pasque on 2008-02-11
You can also try OSS4 if you can't get your problems with ALSA solved.

If you want to try building the latest ALSA, here is a link to a handy script. You would need to modify it for intel-8x0 instead of hda-intel though.
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=24](http://ubuntuforums.org/showpost.php?p=4298894&postcount=24)

---

### Post by nakerlund on 2008-02-14
That alsa building script made it alot easier to build the latest alsa... Unfortunately, the latest version didn't make any difference for me :(

Next, I followed your excellent OSS4 guide. Everything went smoothly but still no sound.. The bars in ossxmix move when I play some sample .wav in totem(set to repeat) but that's it. I tried all jacks (line out, speaker and microphone) but nothing in any... except some static when changing between them.

I haven't had any reason to before, but now I checked in on my [bios firmware]("http://www.giga-byte.com/Support/Motherboard/BIOS_Model.aspx?ProductID=1881") and it seems that there was an update to its DMI in ancient times that I don't got.

> but have you installed any of lib curses for c , rubu and python  Nopes... only the shared libraries. I'm trying them out now!

> I am having the same exact problem except I have a 32-bit system. Have you noticed that when Ubuntu starts the startup sound plays and then you get no sound afterwards? I am having that issue. Sorry for no ideas on how to fix it. I don't even get any attempt to play a startup sound, I'm afraid :(

---

### Post by StGoy on 2008-02-15
I have the same problem with my laptop.  Compaq 700Z with an VIA AC97 chipset.

I don't think I can add much to the conversation since I'm quite new to linux, slowly learning (found a lot of usefull debugging infos in here).  But I can vaguely retrace the apparering of my bug : After a clean install from a 7.10 cd, my sound did work.  I then configured my wifi network and installed all the software updates I could find.
The problem is I can't recall if the problem appeared right after I updated, or after I started fiddling with the installed packages 

Feel free to ask me for more details if needed, I'll be keeping an eye on this thread

---

### Post by StGoy on 2008-02-21
Found my problem (which was a real joke.. can't believe how much of a noob this makes me :| )

Opened Volume control under gnome : While the master sound was on, everything else had been muted... I turned PCM back on and voila, sound problem is resolved..

Kinda doubt you have the same problem nakerlund, but who knows!

---

### Post by dannystaple on 2008-03-25
Okay people, I was having this problem and now found an answer. It may not be a software issue - seriously. If the motherboard has front audio connectors, and you are not using them, then ensure the jumpers are in place to stop it routing audio to the front. Check your board manual - my Gigabyte k8ns had exactly this issue.

Big thanks to [this post](http://ubuntuforums.org/showpost.php?p=1901025&postcount=8) for prompting me. I had not even thought it was such an issue.

---

