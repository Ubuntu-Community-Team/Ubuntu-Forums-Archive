---
title: "Guild Wars Help"
date: 2007-11-10
forum: Wine
---

### Post by lazyrussian on 2007-11-10
I have a dual-partition laptop (7.10 and XP). I have Guild Wars installed on my XP partition - The partition is mounted at all times. Is there a way to run "Gw.exe" with Wine or any other "emulator-esque" on ubuntu using the files that are installed on my XP partition (I don't want to have to reinstall GW on linux)

Thanks!

---

### Post by Inkpot on 2007-11-10
I'm in the same boat....I launch Guild Wars from my Vista partition, but for some weird reason none of the character models show up, only cloaks? Anyone got a solution?

---

### Post by lazyrussian on 2007-11-10
wait, you're able to launch GW on linux through your vista partition?

---

### Post by Inkpot on 2007-11-10
Yessir. I just locate the .exe using Wine and start it right up. Just no character models can be seen. :)

---

### Post by dfreer on 2007-11-10
I'm thinking because of the way guild wars streams game data, it probably not good to run it from a windows partition. Why not just copy the game folder into Ubuntu instead, this way if wine were to somehow corrupt your guild wars install, at least you're windows version will be ok.

---

### Post by Ferrat on 2007-11-10
> **Inkpot said:**
> I'm in the same boat....I launch Guild Wars from my Vista partition, but for some weird reason none of the character models show up, only cloaks? Anyone got a solution?

Do you have a ATi grafic card?

there is a problem with wine after 0.9.45 that makes models disapear.

---

### Post by Inkpot on 2007-11-10
> **Ferrat said:**
> Do you have a ATi grafic card?

there is a problem with wine after 0.9.45 that makes models disapear.

Ah...yes, I have an ATI X1300 Pro. Rats...hopefully, they'll release a bugfix...Playing Guild Wars is one of the few reasons why I switch back to my windows partition. :)

Thanks for the heads up, though. :)

---

### Post by Ferrat on 2007-11-11
> **Inkpot said:**
> Ah...yes, I have an ATI X1300 Pro. Rats...hopefully, they'll release a bugfix...Playing Guild Wars is one of the few reasons why I switch back to my windows partition. :)

Thanks for the heads up, though. :)

I've managed to get my guild wars to show the models but text is still bugged, try these settings  in regedit
See if you can see the models, if not try adding the Disabled Ex... option to the key OpenGL (The one right below) aswell 

If you don't have these keys and strings just create them in the same place as use see them in the screenshot

Please let me know if you get model and what keys you used, this will help in getting the bug fixed =)

---

### Post by lazyrussian on 2007-11-11
sorry for being totally noobish about this but how do I get wine to execute my Gw.exe that's installed on my XP partition.

Do I just opena  terminal and type
```
$ wine /media/sda1/Program\ Files ....GW.exe
```

---

### Post by Inkpot on 2007-11-11
> **lazyrussian said:**
> sorry for being totally noobish about this but how do I get wine to execute my Gw.exe that's installed on my XP partition.

Do I just opena  terminal and type
```
$ wine /media/sda1/Program\ Files ....GW.exe
```

Well, what I did was navigate to the Guild Wars folder on my Vista partition under Ubuntu, right-clicked on the .exe and selected "open with" and then chose Wine.

And Ferrat, I'll give your suggestion a shot. Thanks! Here's to hoping.... :)

---

### Post by lazyrussian on 2007-11-11
> **Inkpot said:**
> Well, what I did was navigate to the Guild Wars folder on my Vista partition under Ubuntu, right-clicked on the .exe and selected "open with" and then chose Wine.

And Ferrat, I'll give your suggestion a shot. Thanks! Here's to hoping.... :)

Alright, I did that and Guild Wars starts. I too have an ATI card, but I have a different problem.

Guild Wars launches at a super high resolution - I have a widescreen laptop (1280x800), but it launches at somehting closer to 4x that size, so (5120x3200) - so I can't see anything,I can't exit, nor can I change my options, plus eveyrhitng is a bit slow.

So how do I do the following:

1) Tell Wine to start Guild Wars ate my normal resolution (I tried using the Wine options but that didn't work)
2) I have Compiz as my defualy windows manager - is there a way I can drop down to the normal gtk/gdm windows manager (so I free up some graphics processing power) without having to turn off every compiz feature one by one.

Thanks!

---

### Post by lazyrussian on 2007-11-11
Ok, I installed fusion-icon and that lets me toggle compiz (on/off) so problem 2 is solved. Now to get Guild Wars to load in the proper window resolution...

---

### Post by seodavid on 2007-12-21
I have it running fine, fps and graphics settings I had to lower, mostly probably due to all the other stuff I have running, I have installed core Microsoft Fonts, I have winecfg set to XP instead of 2000, sound emulation checked. apart from that cannot see what else would effect, unless some added bonus of the way I installed Compiz Fusion affected it.

Screenshots can be found here:
[http://www.iguardians.co.uk/cgi-bin/ikonboard.cgi?act=ST;f=19;t=77;r=1](http://www.iguardians.co.uk/cgi-bin/ikonboard.cgi?act=ST;f=19;t=77;r=1)

---

