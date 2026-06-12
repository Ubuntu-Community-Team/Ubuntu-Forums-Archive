---
title: "Diablo 2 Problems"
date: 2008-07-22
forum: Wine
---

### Post by Joshgo on 2008-07-22
Hi, I am having some problems with Diablo 2 and a program. I've installed Diablo 2 with no problems, and have played it with wine 1.1.1 smoothly. The problem I'm having is that programs such as "autotele" will not work unless I directly launch diablo from the directory. Also, it only works under normal mode "can't use -window" so It's rather annoying that I have to use full screen because I can't even alt tab without causing problems "once I alt tab out of diablo, I can't alt tab back in and also experience other problems". The only way I can use auto tele is if I go full screen, and launch it directly from the directory. I am also using xfce4 on Ubuntu 8.04 rather than gnome.

I've also tried launching diablo from terminal by using the following command

```
env WINEPREFIX="/home/jogo/.wine" wine "C:\Diablo II\D2Loader1.12.exe" -window
```

I've also tested opening Diablo 2 by using the command above with slight modifications (not using "env wineprefix", taking out "-window" etc..) and nothing seems to work. If anyone knows what the problem is, it would be a big help because playing fullscreen without being able to alt tab is really inconvenient. On windows, I would have no problem alt tabbing.

---

### Post by karth on 2008-07-22
AFAIK the switch to play in windowed mode is -w

---

### Post by Joshgo on 2008-07-22
Either way it works, I've used both before. And what is "AFAIK"?

---

### Post by karth on 2008-07-22
It means As Far As I Know

By the way, the best "windowed mode" experience I had with D2 under Wine was with a Wine desktop. The native windowed mode kept on disappearing

---

### Post by evets25 on 2008-07-22
Also, YMMV (Your Mileage May Vary) while using the D2loader, as this is not really supported by... well, *anything*. All the wine test are for wine without the mods, and by using D2loader, you *will* experience additional problems running wine diablo under wine. 

As far as your problems go, my only suggestion is don't use D2loader and windowed mode. They both cause problems. I know, that's not very helpful, but that's all I got, sorry. :/

---

### Post by Joshgo on 2008-07-22
Yeah, I've forgot to mention that I've tried running Diablo using a wine desktop resolution. Either way like I said works fine, the only problem is that the auto tele does not work.

---

### Post by Joshgo on 2008-07-22
Forget what I said just now, I tried to run it under a virtual desktop with wine and it apparently works now. Thanks for trying to help anyways.

---

### Post by rolliespop on 2008-07-27
Do any of you Know if the MH for the new ladder season can work and if so how??  It is annoying trying to rush o MF (magic Find) with out using the MH.

THanks

---

