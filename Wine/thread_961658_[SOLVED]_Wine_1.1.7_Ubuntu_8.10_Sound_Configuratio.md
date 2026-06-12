---
title: "[SOLVED] Wine 1.1.7 Ubuntu 8.10 Sound Configuration Locks"
date: 2008-10-28
forum: Wine
---

### Post by deathpulse on 2008-10-28
I'm having a bit of trouble with Wine 1.1.7 and Ubuntu 8.10 release candidate.  I have the following

VisionTek radeon HD 4870 with latest EnvyNG driver
Asus P5K-E WIFI mobo using onboard sound card
Wine 1.1.7
Ubuntu 8.10 RC with all updates

When I try and use Wine Configuration and go to the sound tab, I can select ALSA or OSS (either produce sound) but when the sound is done playing, Wine configuration is "locked" and I have to force quit the application.  In addition, when I install Team Fortress 2 - the sound works but it is VERY static filled with poor performance.  anyone know what to do?

---

### Post by deathpulse on 2008-10-28
I can obviously provide any output logs - just tell me how and what to post and I will.  No errors are generated on the GUI console - the application just "locks" and must be terminated.

---

### Post by deathpulse on 2008-10-28
Update - I plugged in another soundcard (Diamond Soundcard with C-Media CMI8768 chip) and turned off the motherboard's onboard sound - STILL locks up.  I think the problem is related to the Radeon 4870.  I know the Radeon has a sound interface - has anyone had this problem besides me?  I've re-build the whole OS 3 times now - this never happened with an older NVidia 8800GTS that I had (just replaced it with the Radeon).

---

### Post by deathpulse on 2008-10-28
FIXED!  Ok - I fixed the problem using the following steps:

1.  Delete .wine
2.  selected OSS drivers under wine configuration

Looks like ALSA is buggy with the Radeon 4870.

---

### Post by PayPaul on 2011-09-19
> **deathpulse said:**
> FIXED!  Ok - I fixed the problem using the following steps:

1.  Delete .wine
2.  selected OSS drivers under wine configuration

Looks like ALSA is buggy with the Radeon 4870.


I seem to be having a similar problem. I tried the sound configuration tab and attempted a sound test. I didn't change any other settings and the configuration dialog froze anyway. I can't even quit the wine configuration program. It just sits there. I have a Creative Xi-Fi Extreme but I don't know if that's the problem. Any ideas how to quit the program? How does one do what you did in step 1. Go into terminal?
:confused:

---

