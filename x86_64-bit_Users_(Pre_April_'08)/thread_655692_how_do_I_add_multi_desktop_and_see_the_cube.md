---
title: "how do I add multi desktop and see the cube?"
date: 2008-01-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by mrchaos101 on 2008-01-01
Ok I have the advanced graphics going on this.  Is kinda cool....  I know i have 2 desktops atm.  When I point my mouse on an empty spot on my desktop and use scroll mouse it will flip.

How do I add the 2 other desktops adn then do the whole cube thing where you can zoom back and rotate the cube?  I have gone into my settings and put a check mark on the cube.

Thanks

Oh,  and is this the right forum for noobs?  I mean basic stuff?

---

### Post by ~LoKe on 2008-01-01
This is for people running 64bit ubuntu and have questions relating to 64bit applications.  I would suggest this post being in the general help section, but I suppose I can help you here.

Do you have ccsm installed?  alt+f2, type ccsm in the launcher dialog.  Now you should be able to go to the desktop cube settings, and change horizontal value to 4 (or more, depending on how many sides you want).  For the cube zoom in and out, there should be a zoom slider as well..

Sorry I can't be terribly specific; I don't have compiz installed anymore.

---

### Post by laney on 2008-01-01
Hold your left + right mouse buttons while over an empty area of your desktop and move the mouse. This should spin the cube. Ctrl+alt+<left/right arrow> should change desktops.

Settings for key bindings and such are in System -> Preferences -> Advanced desktop settings. You want "rotate cube". Click on it then look under "Actions".

You can have 4 desktops by right clicking on the switcher in the bottom right, going to properties and adding to the columns or rows. I have 4 columns and 1 row, which makes a normal cube in compiz.

---

### Post by jespdj on 2008-01-03
With "ccsm", ~LoKe means "compizconfig-settings-manager". If you haven't installed it, do:
```
sudo apt-get install compizconfig-settings-manager
```
Then go to System / Preferences / Advanced Desktop Effects Settings. There you can configure the Compiz Fusion effects in detail. The cube is disabled by default. Note that to get the cube working, you need to go to General Settings first and set the desktop to 4 workspaces.
> **mrchaos101 said:**
> Oh,  and is this the right forum for noobs?  I mean basic stuff?
No, this forum is specifically about 64-bit Ubuntu.

---

