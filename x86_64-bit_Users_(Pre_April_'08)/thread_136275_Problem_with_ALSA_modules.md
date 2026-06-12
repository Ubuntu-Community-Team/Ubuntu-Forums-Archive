---
title: "Problem with ALSA modules"
date: 2006-02-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by loco on 2006-02-25
Hi all, I installed Ubuntu for amd64 about a week ago, so im really noob on linux :cool: 
Here is my problem:

Everything was working perfectly until I decided to install the Nforce sound drivers (nvsound) for my realtek alc 850 integrated sound card. Then i had no sound on games, ALSA didnt work, and I didnt know how to fix it. 

So i removed the nvsound.ko module, and installed the realtek linux audiopack 3.5-6. ALSA worked again, but with 1 sound only at a time

After rebooting, if i do lsmod | grep snd I get:

snd_intel8x0           35072  1
snd_ac97_codec         87384  1 snd_intel8x0
snd_pcm_oss            52384  0
snd_mixer_oss          18176  1 snd_pcm_oss
snd_pcm                91276  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24328  1 snd_pcm
snd                    59144  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10912  1 snd
snd_page_alloc         10760  2 snd_intel8x0,snd_pcm


BUT if I do sudo /etc/init.d/alsasound restart, I can play more than 1 sound at a time with alsa, and everything works fine again. After alsasound restarted, there are some modules missing:
lsmod | grep snd
snd_intel8x0           35072  1
snd_ac97_codec         87384  1 snd_intel8x0
snd_pcm                91276  2 snd_intel8x0,snd_ac97_codec
snd_timer              24328  1 snd_pcm
snd                    59144  6 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
soundcore              10912  1 snd
snd_page_alloc         10760  2 snd_intel8x0,snd_pcm


So I think that snd_pcm_oss and snd_mixer_oss are the problem, cause i can play multiple sounds at a time with them unloaded but only 1 sound at a time with them loaded.

¿How can I remove them, or prevent them for running automatically after reboot? I tried rmmod , modprobe -r , and nothing worked: they are still loaded after reboot


Thanks and excuse my horrible english :cry:

---

### Post by queenorych on 2006-02-27
it is my understanding that the nvidia drivers are oss only.  That is they are not ALSA drivers.  If you want alsa you must use the intel AC97 alsa drivers (default )

---

