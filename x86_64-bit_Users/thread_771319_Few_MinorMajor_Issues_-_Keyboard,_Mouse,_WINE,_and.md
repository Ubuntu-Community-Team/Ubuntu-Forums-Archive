---
title: "Few Minor/Major Issues - Keyboard, Mouse, WINE, and Videos."
date: 2008-04-27
forum: x86 64-bit Users
---

### Post by MalachiAD on 2008-04-27
Ok so. I've been using Ubuntu 8.4 (Hardy 64) for about the last week and love it. However, there's some problems that I can't seem to find any information about no matter where I look, so I was hoping you guys might be able to help me out. :)

**1.) WINE Keyboard & Mouse Problem.**
I found other people having similar problems, but not quite this same one. No matter what I do outside of WINE, my keyboard and mouse are fine, responsive and accurate. However, when I load up WINE, a few games have major problems (most games actually) with my mouse and keyboard sticking. Occasionally I can't hold down both mouse buttons to run in Unreal Tournament, can't walk or click things sometimes in World of Warcraft, and it also will randomly hold down keyboard keys when I barely tapped the key maybe once. It's not so much that the keys are seemingly "Sticking", as they are just not responsive sometimes at all. I normally have to click a mouse button like three or four times before it does it, or hit a key like three times before it works (Unless I am typing something in an in-game chat box or something).


**2.) Internet Videos.**
Ok so, when I installed Ubuntu things like Youtube wouldn't work as far as videos go. I went looking, found a fix, and fixed that ~ Youtube works now...but it's the only video site that works now. Myspace videos, and flash videos on any other site, just don't work.

Any help is greatly appreciated, thanks. :)

---

### Post by MalachiAD on 2008-04-27
Also, just to add, because I just noticed one more issue. It seems I also cannot do key combinations in games at all. Like in World of Warcraft I cannot hold CTRL and do a left mouse click, or CTRL+F1 for my keybindings. It will register keys in singles sometimes, but not all the time.

---

### Post by Fredizdman on 2008-05-05
I'm not sure if your mouse/keyboard issue relates, but apparently theres a package installed that new to 8.04 called 'mouseemu', which for some odd reason (probably a bug) disables your mouse when you're pressing buttons on your keyboard. I thought my issue was specific to WINE as well, mostly due to the fact that that is the only time I hold 'W' and try to move the mouse, but if your issue is the same, then trying this even on your desktop will result in the same behavior.

In any case.....

```
sudo aptitude remove mouseemu
```

should immediately resolve your problem....It did for me!

---

