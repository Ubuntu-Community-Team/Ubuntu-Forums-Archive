---
title: "Not recognizing nvida hdmi sound in Alsa Mixer"
date: 2009-04-10
forum: x86 64-bit Users
---

### Post by hieu2ueih on 2009-04-10
Hi,

I am new to Ubuntu and I've been trying to get sound through my hdmi cable. I know it works because it works in Vista. I have an Asus U6sg-A1 with alsamixer v1.0.19 and the NVidia 180 driver. 

This is what I get when I do an aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by fooman on 2009-04-12
try the gnome-alsamixer....it is available from synaptic (system > administration > synaptic package manager - search for "gnome-alsamixer").  or just open a terminal (applications > accessories > terminal) and type or copy/paste the following:

```
sudo apt-get install gnome-alsamixer
```after it installs,  find it in applications > sound & video...open it and check that IEC958 is checked off.  also see if there are any settings there for hdmi or digital and enable/turn them up to max.

hope that helps.

---

### Post by hieu2ueih on 2009-04-13
nope that didn't work either. :-/

---

### Post by Clancy_s on 2009-04-14
I've been researching sound on these forums because of problems I've been having, not yet got to hdmi myself.  Apparently the solution will depend on which version you have.  It's 8.04 or later there's a very thorough post, including hdmi discussion, here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

