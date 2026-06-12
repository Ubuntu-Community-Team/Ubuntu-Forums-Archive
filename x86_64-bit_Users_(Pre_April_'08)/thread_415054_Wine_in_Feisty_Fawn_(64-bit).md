---
title: "Wine in Feisty Fawn (64-bit)"
date: 2007-04-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Garyu on 2007-04-20
OK, so of course I want Wine to work with my fresh 64-bit install of Feisty. So here's what I did:

1) sudo apt-get install lib32asound2
2) wget [http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine_0.9.35~winehq0~ubuntu~7.04-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine_0.9.35~winehq0~ubuntu~7.04-1_i386.deb)
3) sudo dpkg --force-architecture -i wine_0.9.35~winehq0~ubuntu~7.04-1_i386.deb 
4) winecfg

Then I tried running
wine WoW.exe
So the game starts, but it is like very low resolution and interlaced graphics, so it looks like crap. The sound works though... 

Someone who has a good idea on how to improve the graphics here?

EDIT: Issue resolved by itself for unknown reasons. Possibly reboot or Beryl conflict.

---

### Post by RobinOfSweden on 2007-05-04
What did you do to fix your resolution etc?
Good to know any possible fixes out there :D

---

### Post by Garyu on 2007-05-05
oh, I totally forgot about this thread. I will mark it resolved now. :)

funny thing, the screen was all borked the first few times I tried, but then it was fine. And I don't remember doing anything in particular. Maybe I just rebooted the system after installation or something. What I do know is that some games have performing rather strangely when run from Beryl window manager. So now I always switch to Metacity whenever I want to start a game. That might be the difference. Because now, as I said in another thread, everything works great. It was only the first couple of times I tried to start WoW that the screen was all interlaced and strange.

---

