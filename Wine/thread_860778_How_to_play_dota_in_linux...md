---
title: "How to play dota in linux??.."
date: 2008-07-15
forum: Wine
---

### Post by husnan711 on 2008-07-15
i'm still noob in linux..need anyone help me to configure dota in linux..thnxx

---

### Post by Sef on 2008-07-16
Moved to Wine.

---

### Post by Akingboy on 2008-07-16
Go buy warcraft 3 + Frozen Throne and follow the guide in the wine website which is down atm. Then join game with map DotA and play.
You are great example of what people are like who play dota.

Omg this fits so damn nice here:
[http://www.catb.org/~esr/faqs/smart-questions.html](http://www.catb.org/~esr/faqs/smart-questions.html)
Read that and ask again.

---

### Post by NilsHG on 2008-07-16
install wine
in terminal run: winecfg
that creates the settings folder for wine

then pop in the wc3 cd and run wine /dev/cdrom0/setup.exe or whatever is the path to your cdrom drive and or the setup/install exe.

do the same with the TFT addon.

to run wc3 tft open terminal, navigate to your wine folder /home/username/.wine/drive_C/Programs/Warcraft_folder/

then run: wine FrozenThrone.exe -opengl

the commands are not 100% on filenames and on directories.. but you can figure it out. the important things are:
1. run winecfg at least once - in winecfg you can adjust how wine handels the windows programs. 
2. use the option "-opengl" when starting TFT - linux does not know directx

wc3 runs fine on my system and on my old notebook.

---

### Post by SBFC on 2008-07-16
> **Akingboy said:**
> Go buy warcraft 3 + Frozen Throne and follow the guide in the wine website which is down atm. Then join game with map DotA and play.
You are great example of what people are like who play dota.



Heh, I used to play DOTA...funny comment.

---

### Post by h711 on 2008-07-18
wat a nice ans...thnx all..

---

### Post by qousay on 2009-12-27
Nice! Same as what I did with mine.. Just sharing! You can always use wine and if it does not work.. You also can crossover.. However, I prefer to use wine and how i did was documented on my journal blog at [how-to-play-dota-on-linux]("http://pollabs.blogspot.com/2009/12/how-to-play-dota-on-linux.html").

Have a nice game!

---

