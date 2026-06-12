---
title: "Microphone problems: Wine + Vent and in general"
date: 2006-10-23
forum: Wine
---

### Post by mb108 on 2006-10-23
I'm lucky enough to have WoW running perfectly under wine 0.9.19 thanks to the [official Howto]("http://ubuntuforums.org/showthread.php?t=120615"). 

I got the Ventrilo client up with [this Howto]("http://www.ubuntuforums.org/showthread.php?t=41737"), but I could only hear one at a time. Found [this Howto]("http://ubuntuforums.org/showthread.php?t=44753"). Fixed. (My current asound.conf is taken from this howto if you want to check it out).

Winecfg is setup to use OSS only, and I run both with "aoss wine ...", and both run great -- some minor glitches when switching but no big deal.

Now I've gone out and gotten a mic to add into the equation.
I did some fiddling with alsamixer and I can now hear myself through the speakers.

However, Vent does not recognize any input from the mic at all, giving a popup stating "Open input wave device failed" when I try to test it.

Here is the vent setup:
output device: alsa-oss
input device: Default wave mapper (alsa-oss not given as an option)
Hardware input mixer: alsa-oss
Mux: rec
Line: mic


Also of note: 
* Gnome sound recorder, upon pressing "Record", pops up with "Could not get/set settings from/on resource." 
* I tried "arecord test.wav" and got this:
```
Recording WAVE 'test.wav' : Unsigned 8 bit, Rate 8000 Hz, Mono
arecord: set_params:896: Sample format non available
```

.... but like I said, I can hear myself fine through the speakers. :???: 

I have fiddled with creating an asound.rc file based on [this Skype howto]("https://help.ubuntu.com/community/Skype?head-d4579c728d2b7b5f5fd567d30e3c1f2dbdbdd387#head-d4579c728d2b7b5f5fd567d30e3c1f2dbdbdd387"), and feel that I may be on the right track, but I don't know enough about this to really get very far.

Thanks for any help!

---

### Post by minisori on 2006-10-24
You are changing the volume to the playback not to the capture, so you can leave it at 0 (unless you want to hear yourself :p )

When you run alsamixer be sure you check the Mic boost, wich is just at side of the mic one (pressing m if im not wrong).

Now look in the top-left corner, where it says view:. As you see is marked the plaback, so press tab to go to the capture view. Now go to the microphone volume and get it higher.

After this i think you will be ok with the microphone.

---

### Post by mb108 on 2006-10-25
Update:

I misreported some info. Right now Winecfg is set up with both Alsa and OSS enabled, I run "aoss wine /.../Wow.exe" and "wine /.../Ventrilo.exe". I get sound from both, but when I try to setup my mic in Vent, it pops up with "WavInGetDevCaps Failed".

Under the Vent setup, Output Device is "dmixer" (which I believe is Alsa), but Input Device is "Analog Devices AD1986A", which I'm pretty sure indicates that it is trying to use OSS (Alsa would be dsnooper, right?).

I double checked my alsamixer settings, I have mic and capture enabled (in the capture tab), w/ capture turned all the way up. There is no volume setting for mic, and I do not have a mic boost setting -- I believe this is hardware dependent. My sound card sucks.

I have a hunch that it is a deeper issue than alsamixer (asound.conf?), as both Gnome Sound Recorder and arecord are having issues accessing the mic.

Thanks!

---

### Post by louisgag on 2008-08-19
So, after many attempts to get the right configuration it seems that ventrilo finally detected my microphone under wine.

1. kill the pulse audio process
2. set wine to run with oss sound driver
3. run ventrilo under aoss

---

### Post by midtown on 2008-11-05
> **louisgag said:**
> So, after many attempts to get the right configuration it seems that ventrilo finally detected my microphone under wine.

1. kill the pulse audio process
2. set wine to run with oss sound driver
3. run ventrilo under aoss

You are my HERO, I tried about 100 different things in an attempt to get my microphone to work with Rosetta Stone under wine, and this did it! =D>

---

