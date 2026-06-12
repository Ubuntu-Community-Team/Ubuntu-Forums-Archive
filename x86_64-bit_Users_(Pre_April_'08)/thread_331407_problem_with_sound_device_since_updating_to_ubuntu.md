---
title: "problem with sound device since updating to ubuntu feisty on amd64"
date: 2007-01-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by jonah1980 on 2007-01-04
hi i've got amd64 and i installed skype when i had edgy. since updating to feisty i get an error when trying to make a call:  "problem with sound device"

i get this output also in the terminal:
jonah@jonah-desktop:~$ skype
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:ICH
ALSA lib ../../src/confmisc.c:1105:(snd_func_refer) Unable to find definition 'defaults.pcm.dmix_format'
ALSA lib ../../src/conf.c:3500:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib ../../src/conf.c:3957:(snd_config_expand) Args evaluate error: No such file or directory
ALSA lib ../../../src/pcm/pcm.c:2143:(snd_pcm_open_noupdate) Unknown PCM dmix:ICH


i've got all the ai32-libs installed and also i've tried skype on OSS in settings menu instead of ALSA but still not working. Please can anyone help me out??

---

### Post by hpw on 2007-01-20
try deleting .alsa* from your home directory.

that fixed it for me.

br

HPW

---

### Post by hpw on 2007-01-20
ups .. should mean "delete .asoundrc* from your home directory" ....

---

### Post by Seiti on 2007-05-08
Hey! Thanks! 
I was having the same problem here.

The Ubuntu updating system should get rid of these files for us!

---

