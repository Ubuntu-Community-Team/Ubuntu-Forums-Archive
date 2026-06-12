---
title: "HL2 Fails to start"
date: 2007-12-13
forum: Wine
---

### Post by FreewheelinFrank on 2007-12-13
I've just installed Wine and HL2. 

Entered my username and password into steam OK.

After 'Preparing to launch HL2' the screen resolution changes, but then..... nothing.

I tried to launch Steam in a terminal but got an error message:

Fatal error: could not load module 'bin/vgui2.dll'

Is this the right command to launch Steam in a terminal?

wine '/home/user/.wine/drive_c/Program Files/Steam/Steam.exe'

Thanks for any help.

---

### Post by FreewheelinFrank on 2007-12-14
I managed to start Steam.exe with Wine by navigating to the Steam directory (using ls -a to view hidden files and cd 'Program Files' to avoid the space in the name causing a problem) and Steam starts OK. However, when I try to start HL2, I get an error message saying that the Registry is already in use.

If anybody can help, I'd be very grateful. Ta!

---

### Post by FreewheelinFrank on 2007-12-15
I updated to Wine 0.9.51 and now get the Valve screen (no sound) and the loading screen and a lot of HD activity, but then the HD activity stops and the game stalls at a black screen with mouse pointer.

Be grateful if anybody has any ideas. :confused:

---

### Post by aoanla on 2007-12-15
Before you click "Launch" in Steam, click "Properties" and then add "-dxlevel 81" to the launch options. That might should fix your black screen issue.

---

### Post by FreewheelinFrank on 2007-12-15
> **aoanla said:**
> Before you click "Launch" in Steam, click "Properties" and then add "-dxlevel 81" to the launch options. That might should fix your black screen issue.

Thanks for that.  "-dxlevel 81" didn't, but I tried  "-dxlevel 70", and that got me to the game menu. Trying to start a new game caused the computer to stall with the fan working hard. Eventually a HL2 screen came up after a few minutes but no game.

Half Life Source works with the  "-dxlevel 70" setting and seems quite playable.

Fixed the lack of sound by selecting ALSA in Wine config.

I wasn't expecting a lot because my laptops video card (ATI X1600) seems to have a pretty crappy Linux driver.

This computer plays HL1 in Linux as well as my previous computer played HL1 in Windows five years ago, so it looks good for any computer purchased in the future to be able to play HL2 under Linux.

---

### Post by aoanla on 2007-12-15
Well, you've probably been hit by the "using ATI in Linux" bug! 
I had no end of problems with my (higher end than yours - an X1950) ATI card, but things Just Work with my new, non ATI card. 
A new driver release is promised from ATI sometime this month, so...

---

### Post by FreewheelinFrank on 2007-12-16
> **aoanla said:**
> Well, you've probably been hit by the "using ATI in Linux" bug! 
I had no end of problems with my (higher end than yours - an X1950) ATI card, but things Just Work with my new, non ATI card. 
A new driver release is promised from ATI sometime this month, so...


...fingers crossed. 

Thanks for the info.

---

### Post by Brynster on 2007-12-16
It might help if you set wine to run as win2k

open terminal type winecfg (don't worry about the messages that pop up in the terminal window.

When the "Wine Configuration" window opens on the Applications tab at the bottom there is a drop down list of the available types of windows that wine will emulate (yes i know its not actually an emulator lets leave the specifics for later please)in that drop down list select Windows 2000, I fond this speeds up most Steam and Source based games up nicely on my system.

 I hope this helps a little

---

### Post by FreewheelinFrank on 2007-12-16
Yes, I've tried both Win2k and XP. (The configuration panel is also available via Applications>Wine.)

As aoanla mentioned, I'll have to wait and see how the new drivers perform, but I expect I'll be keeping my Windows partition, just to play HL2. The bummer is that despite playing HL2 pretty well, Episode one locks up every five minutes and chews up a fresh section of HD.

Anyway, useful to have Wine for any Windows apps I need to run (and possibly for gaming down the line). Cheers for the help.

---

### Post by Envergure on 2007-12-29
> **FreewheelinFrank said:**
> Thanks for that.  "-dxlevel 81" didn't, but I tried  "-dxlevel 70", and that got me to the game menu. Trying to start a new game caused the computer to stall with the fan working hard. Eventually a HL2 screen came up after a few minutes but no game.

Half Life Source works with the  "-dxlevel 70" setting and seems quite playable.

How do you change the launch options? When I click on "set launch options" I get a dialog saying "these options are for advanced users only" and a text box.  What do I do there?

---

