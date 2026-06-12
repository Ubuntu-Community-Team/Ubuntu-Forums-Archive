---
title: "Fl studio 10 wine sound help?"
date: 2013-03-06
forum: Wine
---

### Post by pokemoncatdog on 2013-03-06
Hi,

I have Linux Mint 13 (Ubuntu 12.04)  mate desktop 1.2.0.3+precise

Have installed fl studio 10 with wine 1.4-ubuntu4.1

I want to be able to use fl studio and say vlc or youtube at the same time. Is there a way to set up sound drivers to so? If not may just give LMMS a try.

I have the sound working in Fl studio 10 by doing:

How to install fl studio 10 on wine with working sound:
[http://forum.image-line.com/viewtopic.php?p=721289](http://forum.image-line.com/viewtopic.php?p=721289)

1. install wine
2. install winetricks
3. use winetricks to change wine's audio from pulseaudio to alsa
4. install fl studio 10, do not install asioforall
5. open fl studio. First exit all other apps the use sound, if I want sound to work in fl studio. Sound will not work in all other app if fl studio is open. Exit Fl studio to get sound in other apps.

I did not even need to start jack or change audio settings in fl studio 10 to have sound in fl studio 10.

---

