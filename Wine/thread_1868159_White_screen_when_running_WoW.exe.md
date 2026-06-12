---
title: "White screen when running WoW.exe"
date: 2011-10-23
forum: Wine
---

### Post by Docmadness on 2011-10-23
Hey gang,

I'm fighting the urge to switch back to Windows and I FINALLY got everything running in Wine and got World of Warcraft: Cata installed.

I did absolutely everything correct and had an issue running the Launcher or running anything past the launcher.

So I switched to running it directly with WoW.exe and I have sound and cursor but nothing else except a FULL white screen.  I have to ESC to get out of it and I can't find anything anywhere to help this.  

Can anyone help me out with this, please?

---

### Post by ubupirate on 2011-10-23
Are you using an Intel GPU?

---

### Post by Docmadness on 2011-10-23
no I'm running AMD processors and Nvidia graphics

---

### Post by Docmadness on 2011-10-23
I remember seeing some codes that were option to input in the terminal...one was like dx3d or something like that.  I can't find where I saw that so I don't know what they exactly were. 

If anyone knows what I'm talking about and thinks that is the issue, please lemme know.

---

### Post by Docmadness on 2011-10-23
GeForce 7150M / nForce 630M 
AMD Turion 64 X2 TL-60

Thats exactly what I'm running on this.

---

### Post by cwwilson721 on 2011-10-24
Just make sure you are:
[LIST]
[*]Running the proprietary drivers. Not the open source ones.
[*]Running WoW in XP mode (winecfg)
[*]Running WoW in opengl mode (Either edit config.wtf, or append '-opengl' at end of launch command)
[*]NOT running WoW from a NTFS partition.
[*]NOT running WoW with Desktop effects enabled (Choose one of the 'no effects' options for your desktop in the drop down box at the login screen, or if running 11.10, the "gear" icon 
[/LIST]
These 5 simple things straighten out 99% of issues. DO NOT run in Direct X.

If you don't do these, then good luck.

Double check.

---

### Post by Docmadness on 2011-10-24
Yea...I have all that stuff set up correctly.  I can't figure it out at all.  

No matter what I've done, everytime I run wow.exe(because it won't play through the wow launcher hitting the 'play' button), the window opens and I have sound and the cursor even turns to the little gray hand, but the entire screen is white with no options or anything. I can even move the cursor around...it doesn't lock anything up...just has the white screen.

Ive done absolutely everything possible that I've found to do and no luck getting rid of that white screen.

Thanks for your suggestion

---

