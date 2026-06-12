---
title: "Sound kind of working"
date: 2009-05-17
forum: x86 64-bit Users
---

### Post by here.david on 2009-05-17
After many hours of reading trying re-install (back-up image of new Ubntu 9.04 install) to start clean each time....this is as far as I have got...
 
Mplayer GStreamer 0.10.22 sounds works yet must manually start dvd to get it to play
VLC 0.9.9a sounds does not work yet dvd auto starts (also clearer picture)

yet when I try modprobe I get:

root@a6110n:~# sudo modprobe snd-ALC1200
FATAL: Module snd_ALC1200 not found.
root@a6110n:~# sudo modprobe snd-MCP61 High Definition Audio
FATAL: Module snd_MCP61 not found.

On the Mplayer Title bar under sound - language, I see a AUDIO 0 marked with the Auto not mark...in the other players this does not even show up....(yet I have tried everyone I found listed in posts...<grin>....)

Any help....Please....as this is the last issue I have before leaving X64 XPpro/Vista on Desktop and Laptops....printer/scanner/other install items now very easy to set-up which stop all previous moves to Ubuntu...
==================================================
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
==========================================
):P

---

### Post by Yellow Pasque on 2009-05-17
The module for onboard "High Definition Audio" (Intel Azalia compliant) devices is snd-hda-intel and if you have sound, then it's already loaded.

Suggestion for VLC: Install the "vlc-plugin-pulse" package and set VLC preferences to use PulseAudio for the sound backend.

More detail: Start VLC, go to Tools -> Preferences -> Audio menu. Change "Output" from Default to PulseAudio.

---

