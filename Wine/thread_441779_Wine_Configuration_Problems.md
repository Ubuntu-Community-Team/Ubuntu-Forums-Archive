---
title: "Wine Configuration Problems"
date: 2007-05-12
forum: Wine
---

### Post by Teh Dust on 2007-05-12
I have installed wine from synaptic, But when I try to run for the first time, my computer freezes while the terminal says configuring directory .wine

I have no idea why it is doing this.

Compaq Presario SR1222NX
2.93 Pentium 4
Intel 910GL intergrated graphics
512mb RAM

---

### Post by YokoZar on 2007-05-13
Give it some time.  When Wine is first run it needs to make a virtual windows installation and copy some files around in your home directory.

If you think it did freeze (or, the windows application you're trying to run did), you can hit ctrl-c to abort.  Try running "winecfg" from a terminal - that'll create the configuration just like running Wine will, and also allow you to change some settings if you like.  The defaults should be fine, though - hit ok to exit winecfg, then rerun your application and see if it works.

---

### Post by Teh Dust on 2007-05-13
Ive tried waiting and ive tried winecfg, It will freeze no matter what I try to run on it. I cant even ctrl alt backspace when it happens. The only thing I have been able to do is create a blank .wine directory and run regedit.

---

### Post by Sliver85 on 2007-05-15
I'm having the exact same problem.  Ctrl-C does nothing when trying to run winecfg through terminal.

This is a complete computer freeze: mouse can't move, cursor stops blinking.

My Specs:
AMD Athlon 64 X2 4400+ @ 2.2Ghz
2GB Ram
BFGTech Geforce 6800 Ultra

---

### Post by hikaricore on 2007-05-15
Have you tried the 64 bit version of wine from the WineHQ repository?

[http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/)

Direct link: [http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine_0.9.37~winehq0~ubuntu~7.04-1_amd64.deb](http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine_0.9.37~winehq0~ubuntu~7.04-1_amd64.deb)

I know some users have had trouble using 32 bit version on 64 bit systems.

--Aaron

---

### Post by Sliver85 on 2007-05-15
I was already using the 64-bit version from the package repository.  I downloaded it from the link you gave, and that package is the same version and gives the same problem.

---

### Post by Sliver85 on 2007-05-20
Any other ideas on solving this problem?

---

### Post by Sliver85 on 2007-05-28
I don't like to triple post, but does anyone have *any* ideas on solving this?

---

### Post by FallenEdict on 2007-06-30
I'm getting the same problem. Wine freezing up when it's configuring the directory. Were you able to figure out the problem ?

---

### Post by Sliver85 on 2007-07-18
Nope, and I'm hoping someone can come and help us.

---

### Post by billT on 2007-07-18
I've had lockups like you describe when trying to run a game with WINE while using Compiz as my WM. Changing it to metacity fixes the problem. If you're attempting to do something similar, you might try changing the WM.

---

### Post by jusama14 on 2007-12-04
I am also having this same exact problem. Could someone help us out here?

---

### Post by cogadh on 2007-12-04
Don't use Compiz while using Wine. Problem solved.

---

### Post by Sliver85 on 2007-12-04
Actually, I'm not using compiz at all, so that is not the problem.

---

### Post by cogadh on 2007-12-04
Okay then, in that case you probably need to do a complete uninstall and purge of Wine, including the .wine directory, then reinstall:
```
sudo apt-get remove --purge wine
rm -r ~/.wine
sudo apt-get install wine
winecfg
```

---

### Post by Sliver85 on 2007-12-04
Been there, done that.

I've also tried on a completely clean install earlier tonight.  First thing after installing Ubuntu 7.10 was add the wine repo and install it.  Compiz was disabled, and winecfg still locked up the pc.  Then I installed the restricted driver (nvidia-glx-new) and it locked up again.

Thanks for any more help you can offer.

---

### Post by Fred_E _krugar on 2007-12-05
One problem I was having for this problem was the sound card.

I installed wine using the onboard sound then replaced the sound card with no problems.But..............

When on one of my quests through linux land I totally borked my system. No problem I will just reinstall.....Everything worked but when I got to installing wine wtf it keep freezing on config.....ok bad install try a reinstall........no go......Oh ***** I forgot about the sound card, so I took out the sound card, used the onboard sound...Wine installed great did the config thing cool everything working as it should. But damn this onboard sound, sounds like ***** reinstall the the sound card and it is still wourking like a charm in CSS. I hope this helps you guys. It did for me.

---

### Post by Sliver85 on 2007-12-05
We have success!!!!

Thank you so much, my sound card was the problem.  Once I took it out and reinstalled wine, it worked fine.

---

