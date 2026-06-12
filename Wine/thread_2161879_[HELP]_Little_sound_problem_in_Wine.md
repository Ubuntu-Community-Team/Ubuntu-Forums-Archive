---
title: "[HELP] Little sound problem in Wine"
date: 2013-07-12
forum: Wine
---

### Post by protoss96 on 2013-07-12
Hello,

I know that this issues has been posted thousand times, but resolves from that issues didn't helped me. :(

I am using newest Wine version,(sudo apt-get install wine) i think that is final version.
I wanted to install diablo 2, and runned following command:
```
 wine /media/Expansion/INSTALL.EXE 
```
Setup runs fine, but no intro sound :/, i get this from ALSA:
```
 ALSA lib conf.c:3314:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib pcm.c:2217:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dsnoop.c:612:(snd_pcm_dsnoop_open) unable to open slave
 
```

I executed winecfg and pressed 'Test Sound' under Audio tab, i hear sound in wine but no in some windows app, btw all of my Audio options are under 'default'.

 How can i solve this? and thank you for your time :)

---

