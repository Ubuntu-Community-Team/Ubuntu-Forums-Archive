---
title: "No Sound - Sound Blaster Live"
date: 2009-09-22
forum: Wisconsin Team
---

### Post by path2009 on 2009-09-22
I have been working with computers since 1984 but im new to linux. 
I have a sound blaster live card but cant get any sound in 9.04. I got sound from 8.10.
i have checked the forums and others with my problem got no answers. What is the solution to my problem ?. 
Please help me, i hate windows and i want to make the switch to ubuntu permanent but i am still to new and am having a hard time understanding linux. please help me fix my sound problem

path

[EMAIL="web2008@att.net"]web2008@att.net[/EMAIL]

---

### Post by yabbadabbadont on 2009-09-22
Please post the output of the following commands:
```
lspci -knn
```
and
```
lsmod | grep snd
```

---

### Post by PendoLeMellon on 2009-11-13
I also have soundblaster live, and have had sound in ubuntu before. But now, in version 9.10, the sound was gone.

Here is my output from those commands:

lspci -knn

```
lspci -knn00:05.0 Multimedia audio controller [0401]: C-Media Electronics Inc CM8738 [13f6:0111] (rev 10) 
    Kernel driver in use: C-Media PCI 
    Kernel modules: snd-cmipci 

00:0a.0 Multimedia audio controller [0401]: Creative Labs SB Live! EMU10k1 [1102:0002] (rev 04) 
    Kernel driver in use: EMU10K1_Audigy 
    Kernel modules: snd-emu10k1

00:0a.1 Input device controller [0980]: Creative Labs SB Live! Game Port [1102:7002] (rev 01) 
    Kernel driver in use: Emu10k1_gameport 
    Kernel modules: emu10k1-gp  
```lsmod | grep snd

```
snd_emu10k1_synth       6140  0 
snd_emux_synth         32860  1 snd_emu10k1_synth 
snd_seq_virmidi         5628  1 snd_emux_synth 
snd_seq_midi_emul       6332  1 snd_emux_synth 
snd_emu10k1           135136  3 snd_emu10k1_synth 
snd_ac97_codec        101216  1 snd_emu10k1 
snd_cmipci             33408  2 
ac97_bus                1532  1 snd_ac97_codec 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss 
snd_pcm                75296  4 snd_emu10k1,snd_ac97_codec,snd_cmipci,snd_pcm_oss 
snd_page_alloc          9156  2 snd_emu10k1,snd_pcm 
snd_util_mem            4156  2 snd_emux_synth,snd_emu10k1 
snd_opl3_lib           10396  1 snd_cmipci 
snd_hwdep               7200  3 snd_emux_synth,snd_emu10k1,snd_opl3_lib 
snd_seq_dummy           2656  0 
snd_mpu401_uart         6940  1 snd_cmipci 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  4 snd_seq_virmidi,snd_emu10k1,snd_mpu401_uart,snd_seq_midi 
snd_seq_midi_event      6940  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi 
snd_seq                50224  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
gameport               11368  3 snd_cmipci,emu10k1_gp 
snd_timer              22276  4 snd_emu10k1,snd_pcm,snd_opl3_lib,snd_seq 
snd_seq_device          6920  9 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
snd                    59204  24 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
soundcore               7264  1 snd  
```I looked at the output of the second command and recognised the ac97 codec belonging to the integrated sound on my motherboard.

I went to System > Preferences > Sound and, sure enough, I had two sound devices listed under *hardware*.

I went to *input* and *output,* and switched to the second sound device on the list, and now my sound is working again.

---

### Post by k20freakstic on 2009-12-20
ok, i recently had this problem upgrading to 9.10
Check your kernels, and make sure your using the latest one. 
Do a system test, under system. and if it shows up there.
put "aplay -l" and it shows no sound card. it may be your kernels.
good luck.

---

