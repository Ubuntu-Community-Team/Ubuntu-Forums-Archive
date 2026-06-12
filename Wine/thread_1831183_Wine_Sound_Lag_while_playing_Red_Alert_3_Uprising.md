---
title: "Wine Sound Lag while playing Red Alert 3 Uprising"
date: 2011-08-23
forum: Wine
---

### Post by CyberMushroom on 2011-08-23
sorry if this is in the wrong place. i am a noob here in ubuntu forums.

I have installed Red Alert 3 Uprising using wine. It launches perfectly but the sound has this annoying delay and choppiness that you can't understand the dialogue and the sound effects. I have tried using wine1.3 with wine1.3 there is no sound at all. so i downgraded again to wine1.2. i have tried all the audio options in winecfg and found that only alsa and esound works with the same results regardless if full or emulation. now i am stuck at a dead end. also the choppiness in sound causes some lag in the game itself coz when i disable the sound it runs smoothly without any delays. with other games such Warcraft 3, StarCraft 2, CoD4MW and CoD4MW2 i have no problems with the sound. the choppiness only happens with this game. any suggestions? please help.

here are my system specs:

Processor: AMD Athlon II X2 250 3.0Ghz
Memory: 4GB DDR3 1333
Swap Space 4GB
Motherboard: ECS MCP61M-M3
Graphics: Nvidia 9500GT 1GB 128Bit
Operating System: Ubuntu 10.10 Maverick Meerkat
Kernel: 2.6.39-02063903-generic
Wine Version: 1.2.3

I have been an ubuntu user since ubuntu 9.04 and i am happy with ubuntu 10.10 for the time being

---

### Post by howefield on 2011-08-23
Thread moved to the "*Wine*" forum.

---

### Post by CyberMushroom on 2011-08-23
sorry. first time poster. hehehe thanks for moving.

---

### Post by thatguruguy on 2011-08-23
The sound system was completely rewritten for Wine 1.3.26.

In older versions of Wine, you may try adding "padsp" at the beginning of the line calling the game, e.g.:
```
padsp wine /home/fred/.wine/drive_c/Program\ Files/BubbaGames/bubba.exe
```
You will need to have the pulseaudio utilities installed for this to work.

In 1.3.26, you may have some luck trying the following.  First, type the following in a terminal:
```
winecfg
``` 
Then, choose the "Audio" tab. Make sure that "ALSA Driver" is checked, and under "Hardware Acceleration" choose "Emulation."

---

### Post by CyberMushroom on 2011-08-28
> **thatguruguy said:**
> The sound system was completely rewritten for Wine 1.3.26.

In older versions of Wine, you may try adding "padsp" at the beginning of the line calling the game, e.g.:
```
padsp wine /home/fred/.wine/drive_c/Program\ Files/BubbaGames/bubba.exe
```You will need to have the pulseaudio utilities installed for this to work.

In 1.3.26, you may have some luck trying the following.  First, type the following in a terminal:
```
winecfg
```Then, choose the "Audio" tab. Make sure that "ALSA Driver" is checked, and under "Hardware Acceleration" choose "Emulation."

I have tried these 2 already but it is still the same. the sound is really laggy and it slows down. i am back with 1.2 again. emulation and full both output the same sound. any more suggestions? other games here seem not to have the issue. only happens in ra3 and i have already tried to reinstall the game. =(

edit:
oh wait, how do i install pulse audio? i seem to have missed that.

---

### Post by CyberMushroom on 2011-09-02
*bump* anyone? :(

---

### Post by CyberMushroom on 2011-09-12
i've tried the pulse using padsp and have also tried aoss but still the sound is jittery. i have also tried removing wine completely and reinstalling it for a fresh start but still the sound is jittery.

any more suggestions???

---

