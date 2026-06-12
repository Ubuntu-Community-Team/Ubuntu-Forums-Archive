---
title: "USB headset audio quality is awful"
date: 2014-06-18
forum: Wine
---

### Post by immerohnegott2 on 2014-06-18
Hey there. I just got a Logitech headset (h540), which works great with native apps on Ubuntu 14.04. Input and output both worked out of the box, and I haven't had any issues with anything Linux-native.

However - I need to use a ticketing/softphone system for my new job, which only has a Windows client. When I try to use the headset in WINE, the sound is awful. Normal analog speakers sound absolutely fine, though. I've searched a bit, but all of the stuff I've found is ancient and mostly from waay back when WINE let you specify the audio driver/sample rate/driver emulation in WINECFG.

Anyone have a hint on where to start?

---

### Post by immerohnegott2 on 2014-06-18
Fixed it. Didn't notice that the headset exposed four devices to ALSA (S/PDIF Output, Headphones, Microphone, Digital Input). Selecting the S/PDIF and Digital Input devices did the trick.

---

