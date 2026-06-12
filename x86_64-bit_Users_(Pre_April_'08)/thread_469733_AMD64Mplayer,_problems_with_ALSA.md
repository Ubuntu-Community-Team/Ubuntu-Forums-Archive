---
title: "AMD64:Mplayer, problems with ALSA"
date: 2007-06-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by chronosoft on 2007-06-10
hi there, I'm having problems with mplayer playing videos with the alsa driver selected, i keep getting this error pop-up "alsa-control: unable to find simple control 'PCM',0" flashing rapidly.

these are my specs

AMD X2 3600+
2gigs ram
Creative audigy value soundcard
nvidia 7600GT
using Ubuntu 7.04 fiesty AMD64

output from lsmod | grep pcm

snd_pcm_oss 49536 0
snd_pcm 92808 7 snd_ca0106,snd_ac97_codec,snd_usb_audio,snd_pcm_oss

---

