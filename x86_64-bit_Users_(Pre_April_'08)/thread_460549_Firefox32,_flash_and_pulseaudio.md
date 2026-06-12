---
title: "Firefox32, flash and pulseaudio"
date: 2007-05-31
forum: x86 64-bit Users (Pre April '08)
---

### Post by TeKniKal on 2007-05-31
For quite some time now, I have been trying to get this magic combination: Ubuntu Feisty 64-bit with firefox32 (installed with the script), Adobe Flash 9 and PulseAudio working.

I've followed almost any guide on the relevant websites (Pulse Audio, REvolution Linux, even Gentoo). The problem is the following: he doesn't want to play sound through PulseAudio from within Flash (neither from within mPlayer within firefox, but that is of less importance, I think).

So, what I have now are really a load of configuration files which all try to fix this, by several different environment variables (which doesn't harm anybody). I will try to explain what I have tried yet, if somebody has a setup of firefox32, flash and pulseaudio running. please let me know.

1) I tried to load padsp, by using the following code (which gets executed by the firefox32 shell script)
```
export FLASH_FORCE_PULSEAUDIO=1
  export PULSE_BINARY=/usr/bin/pulseaudio
  export RUNTIME_FIREFOX_DSP="padsp"
  export FIREFOX_DSP="padsp"
```This doesn't get me anywhere, it is like it completely ignores the first one (with this enabled, he still uses ALSA; although I have used the patched file from revolution linux (my only hope is that I put it in the right directory)

2) well, since that didn't work, I just tried to fiddle with the ALSA configuration, which seems to work for 64 bit applications (not entirely sure, though). In my also configuration, I set up everything to use pulseaudio, which has to work. But I get the following error everytime:
```
ALSA lib ../../../src/pcm/pcm.c:2106:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_pulse.so

```. So obviously, this doesn't work either. I also tried to use the dmix interface from within ALSA (which alsoe doesn't work: the socket isn't accessable (or something similar, I just give up on dmix sound). This shared library is located where stated, so I can't figure out why he can't open it.

3) over the normal ALSA configuration with pulseaudio killed totally, I do get sound through ALSA. But ALSA somehow locks the sound device so I can't start pulseaudio afterwards (at least until flash has done playing audio), and the other way round: when trying to play through ALSA, it seems that the sound doesn't get passed to PulseAudio (or the local sound device), but I constantly use the same ALSA configuration.

So my question: has anyone got some tips to fix this (besides turning pulseaudio on and off), the ideal situation would be if Flash could direct its audio to PA directly, but anything that lets me forward this audio to PA will do. 

If I need to provide any more information, concrete configuration files, just ask :-)

Thanks in advance

---

### Post by promet on 2007-06-27
try the Flash reference hear:

[http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

---

### Post by enderandrew on 2007-06-27
Given how much of a pain Flash is in 64, and given that apparently there is no sun-java6-plugin for 64 users, maybe I should try to get Firefox 32 working.

Is there a good guide for this somewhere, or should I just download source, adjust my CHOST and compile?

I'm assuming that once I have a Firefox 32-bit build working, it can direct me to the appropriate plugins regardless of whether or not they are in the Kubuntu repositories.

---

### Post by TeKniKal on 2007-06-27
Flash is rather a pain in any 64-bit installation, even in Firefox32. I recommend you use the Firefox32 scripts which linger on this forum (just search for them, they are quite famous around here). They also had an option to install Flash and Java if I'm not mistaken.

---

### Post by TeKniKal on 2007-06-27
> **promet said:**
> try the Flash reference hear:

[http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

I already tried that, both Flash7 and Flash9 parts, but I don't get them working.

Ah, well, I kind of used to "killall pulseaudio", the only additional annoyance is that Firefox32 hangs if I do it too late (i.e. when Flash has already been loaded to play something).

---

### Post by ZarathustraDK on 2008-02-03
This one worked for me :

[http://blog.paulbetts.org/index.php/2007/06/08/native-pulseaudio-with-flash-9-fix-video-crashes/](http://blog.paulbetts.org/index.php/2007/06/08/native-pulseaudio-with-flash-9-fix-video-crashes/)

Pulseaudio is sweet, I have been struggling with getting multiple sounds for WoW and background-music via aoss forever, then PA comes along and gives it to me in less than 15 minutes.

That's the mark of a keeper.

---

### Post by Cappy on 2008-02-03
Nuke Skyjumper has a guide here: [http://ubuntuforums.org/showthread.php?t=655825](http://ubuntuforums.org/showthread.php?t=655825)

---

