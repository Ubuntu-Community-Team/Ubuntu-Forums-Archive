---
title: "Installing Game under Windows and running under Wine"
date: 2008-03-08
forum: Wine
---

### Post by sonnet on 2008-03-08
Hi guys, on [www.winehq.org](www.winehq.org) web site on the section appdatabase, I've read about a lot of applications and game which have difficulties to install,but once installed they just work fine.So I thought:"what happen if I install a game under windows XP,then copy the folder of that game on an external usb ,and copy back on wine directories on Ubuntu?
What I mean is : on windows usually you can install a game and if you copy the game's folder on another pc with the same os,it will just work.

Can this be done with Wine (to skip the installation difficulties )?
Can this be done with software application that are not game?

---

### Post by YokoZar on 2008-03-08
> **sonnet said:**
> Hi guys, on [www.winehq.org](www.winehq.org) web site on the section appdatabase, I've read about a lot of applications and game which have difficulties to install,but once installed they just work fine.So I thought:"what happen if I install a game under windows XP,then copy the folder of that game on an external usb ,and copy back on wine directories on Ubuntu?
What I mean is : on windows usually you can install a game and if you copy the game's folder on another pc with the same os,it will just work.

Can this be done with Wine (to skip the installation difficulties )?
Can this be done with software application that are not game?
Doing that won't work, not even on Windows.

There's more to a Windows installation than just copying files - stuff like registry entries and other configuration gets copied into the system folders.  You need to install applications into Wine fresh.


That said, most installer bugs should be fixed in Wine.  Was there a particular app you were having trouble with?

---

### Post by Woody1987 on 2008-03-08
I find this to work with some games such as Supreme Commander Forged Alliance and Sins of a Solar Empire. Try it with the games you have.

---

### Post by poofyyoda on 2008-03-08
I do this with most my 'wine software'.  I run them straight from the windows drive.  To help with registry issues, just run regedit in windows and export the tree with all that applications registry values, as '9x/NT4' format and import into wines registry.

---

### Post by sonnet on 2008-03-09
> **poofyyoda said:**
> I do this with most my 'wine software'.  I run them straight from the windows drive.  To help with registry issues, just run regedit in windows and export the tree with all that applications registry values, as '9x/NT4' format and import into wines registry.

Windows xp is NT5.xx kernel, are you sure I should export as '9x/NT4' format?
Which version of Windows are you using?Do you think it'd work even with Vista?

---

### Post by GSF1200S on 2008-03-09
> **sonnet said:**
> Windows xp is NT5.xx kernel, are you sure I should export as '9x/NT4' format?
Which version of Windows are you using?Do you think it'd work even with Vista?

AFAIK, wine can only import those formats at the moment, hence why hes telling you to export in that format.

Some games will run straight after a copy, others will need registry entries exported too...

---

### Post by NightwishFan on 2008-03-09
There is one game I wanted to get working in wine. Arcanum: Of Steamworks and Magick Obscura. The installer never asks for the second cd though. It just copies from the first and informs me it is finished.

---

### Post by GSF1200S on 2008-03-09
> **NightwishFan said:**
> There is one game I wanted to get working in wine. Arcanum: Of Steamworks and Magick Obscura. The installer never asks for the second cd though. It just copies from the first and informs me it is finished.

Put the first CD in and copy it to a folder on your desktop. When it prompts for the 2nd CD, delete the contents from the first folder, and copy the second disk into the folder. Then, click ok and it should keep going...

**EDIT** i misread your post.. you said it never asks... sorry. is there a DVD version available or something?

---

### Post by sonnet on 2008-03-09
> **GSF1200S said:**
> AFAIK, wine can only import those formats at the moment, hence why hes telling you to export in that format.

Some games will run straight after a copy, others will need registry entries exported too...

Thanks for the explanation, now I understand.
Ok after these answers I'll try out this week.

---

### Post by NightwishFan on 2008-03-09
The error is that It refuses to prompt for the second cd at all and finishes the install from the first. The installer must not be compatible with wine. It is no problem. I really do not use wine anymore.

---

