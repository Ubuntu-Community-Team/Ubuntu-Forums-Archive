---
title: "No sound"
date: 2008-10-11
forum: x86 64-bit Users
---

### Post by jarcher on 2008-10-11
I'm not getting any sound. It happened recently, not sure when or what I did to cause it.

Using Realtek onboard sound. :confused:

Help much appreciated.

---

### Post by phlembob on 2008-10-11
I too use on-board sound.  I had a no sound event after updating once.  I use a Foxconn mo-bo att,, ASUS mo-bo before.  A list of your hardware would be nice.  If your sound doesn't come back after a reboot you may have to reload your libs from System>Administration>Synaptic Package Manager.  You will need to investigate it, but beware you can make some things not work in here.  Start with Multimedia...you need to become familiar just like any OS.

---

### Post by jarcher on 2008-10-11
Restarting did nothing.

Mobo: Gigabyte GA-M68SM-S2
Chipset:  NVIDIA GeForce 7025 / nForce 630a chipset
Integrated Peripherals

   1. T.I. IEEE1394 controller
   2. Realtek RTL8211BL Gigabit Ethernet controller
   3. Realtek ALC888 Audio Codec

---

### Post by phlembob on 2008-10-11
The fastest way to take care of the problem is to use the o'fast tech solution; reload your OS from disc.  If you have any info that needs to be saved - save it.  (Don't do a full back up: just the data you can't lose.)  This is the fastest technique most likely.  If you have time to look and become more familiar you should.  Ubuntu 8.04 LTS 64 bit is a solid OS.  I haven't had enough problems to be as familiar as I should.  I read these forms daily.  There are instructions to load many applications in the forms.  No hardware or any OS live in perfect harmony.  Bits get dropped in storage or downloads sometimes (rarely).  Because of this, the user must take up the slack.  Read some forms, you have a great repertoire of experience in them.  There are a few here that can write and organize well. You may want to remember the handles of those people so you can read what they tell others. Take your time or go as fast as you can --- the choice is yours. Let logic be your guide, but keep jammin :guitar:

---

### Post by Yellow Pasque on 2008-10-11
> The fastest way to take care of the problem is to use the o'fast tech solution; reload your OS from disc.
Ubuntu is not Windows. It's a Linux/UNIX-based OS, meaning it's highly modular. Rarely is breaking out the install CD and wiping out all updates/tweaks/customizations the best solution to a problem.

jarcher: post output from these commands to see where to start diagnosing. Most likely, a kernel update caused the problem.
```
aplay -l
sudo lshw -C multimedia
```

---

### Post by nss0000 on 2008-10-11
JA:

My ASUS-m2n never would play onboard sound under DD. I got a $15 SB16 workalike card.

---

### Post by wfp on 2008-10-12
I am using realtek ALC888. Try opening sound preference. Preference> Sound. Now that you have that opened check these default settings under the devices tab. 

Sound Events
Sound playback  > Autodetect
Music Movies    
Sound playback  > Autodetect

Audio Conferencing 
Sound playback  > Autodetect
Sound Capture   > Alsa-Advanced Linux Sound Architecture 

Default Mixer Tracks >HDA Nvidia Alsa Mixer  
I would also double click your sound icon on your panel if you have one and make sure Master-PCM-Front are turned all the way up and not muted.

---

### Post by jarcher on 2008-10-13
Temujin:

aplay -l 
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

sudo lshw -C multimedia  
*-multimedia            
       description: Audio device
       product: MCP67 High Definition Audio
       vendor: nVidia Corporation
       physical id: 7
       bus info: pci@0000:00:07.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel

wfp: Those are my settings.

Oh, and I also should've mentioned in the OP, I dual boot and my sound works fine on Windows.

---

