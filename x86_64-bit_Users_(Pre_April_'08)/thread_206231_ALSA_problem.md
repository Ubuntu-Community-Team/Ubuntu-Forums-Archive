---
title: "ALSA problem"
date: 2006-06-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by magusofdeath on 2006-06-29
hi people.. i have installed the NForce Driver from [www.nvidia.com](www.nvidia.com) and if i will play anyone game like SuperTux or Nexuiz i dont have sound! lauching the SuperTux in terminal i have this:
magus@Slayer:~$ supertux
Datadir: /usr/share/games/supertux
ALSA lib confmisc.c:672:(snd_func_card_driver) **cannot find card '0'**
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
Warning: No joysticks are available.

and lspci
0000:00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
can anyone help me?

Ubuntu Dapper AMD64
Asus A8N-SLI
GeForce 6600 pci-e

---

