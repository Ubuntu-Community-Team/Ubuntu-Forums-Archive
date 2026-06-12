---
title: "Jaunty x64"
date: 2009-04-24
forum: x86 64-bit Users
---

### Post by dougdalton on 2009-04-24
I just install Jaunty and after installing the flash plugin my sound starts but then stops after playing for a second,   I removed the flash plugin and install the flash 64bit alpha and none of my sound works even after removing it??

It may have nothing to do with flash,  my sound only works for a split second when booting up then stops before the ubuntu login starts.... it was working fine after the initial install?

I am running on a touchsmart tx2 

snd_hda_intel         557364  3 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    78792  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm

---

### Post by Favux on 2009-04-24
Hi dougdalton,

See post #72 here:  [http://ubuntuforums.org/showthread.php?t=1038898&page=8](http://ubuntuforums.org/showthread.php?t=1038898&page=8)
Basically you are adding the line:
```
options snd-hda-intel model=toshiba
```
to alsa-base at /etc/modprobe.d/alsa-base.  It works for Intrepid anyway.

Hope this helps.

---

### Post by dougdalton on 2009-04-24
That fixed it perfectly thanks

---

### Post by Favux on 2009-04-24
You're welcome.

---

