---
title: "How to install Battlefield 1942?"
date: 2006-12-16
forum: Wine
---

### Post by Aleksandersen on 2006-12-16
Hi,

I got a copy of *Battlefield 1942 : Deluxe Edition* and I would like to get it to work on Ubuntu.

How can I do this? I have never used a Windows game on Linux before, so bear with me and please explain carefully.

Thanks in advance. :)

---

### Post by Sandlst on 2006-12-18
To run this game, you will need wine, which is an application that allows to run some windows games (but sadly not all....yet!).  Looking at the winehq page for this game, [here]("http://appdb.winehq.org/appview.php?iVersionId=4998") is not very promising; however, trying can't hurt, so I'll try to walk you through it, its not tough.  First open a terminal (Applications/Accessories/Terminal) and copy and paste the following line directly: ```
sudo apt-get install wine
```This will install wine on your computer.  Next, type this line in ```
winecfg
```In the window that opens up, click on the 'Drives' tab, highlight the one that matches the mapping /media/cdrom0, click show advanced, and make sure the 'type' drop down menu is set to CD-ROM.  After this, click ok.  Now, insert your cd, ubuntu should open a folder with the cd's contents.  After it does, look for setup.exe or install.exe, right click it, then click 'open with other application' from the menu.  At the bottom, click the arrow next to 'Use a custom command' and type in```
wine
```After a bit, the game should hopefully start to install. After it is done, everything you install via wine is located in .wine/drive_c area, which looks like a normal windows structure.  An easy way to goto it would be to open a terminal, and paste this in```
nautilus ~/.wine/drive_c/
```You would then navigate to the games folder (probably in Program Files) find the .exe file to launch it, and double clicking that should do the trick, since .exe files *should*  automatically be opened with wine.  That should do it, if the game can indeed be run through wine.  To check if any other games can be run with wine, a good place to go is the App DB section of [www.winehq.org]("www.winehq.org").  Towards the bottom left of the screen is a search bar, it should tell you if a game is compatible or not.  The games marked as Platinum, Gold, Silver, and sometimes Bronze will usually work in wine, the games marked Garbage are almost surely going to fail.  Good luck, post back if you have any problems!

---

### Post by TheTank on 2006-12-18
Any BF42 related question you can also ask as well. I have been playing it since it's release and know my way around the settings.

If you are looking for the best BF42 experiance around, get the following mods (ordered in my personal preferance):
Forgotten Hope (more geared twards realism, imho the best out there)
Desert Combat (desert conflict 2 - 1991)
Eve of Destruction (vietnam)

---

### Post by peregrinogris on 2007-12-19
I would like to know if you can launch BF1942 directly from a windows installation using Wine. 
I mean, I have a WinXP and Ubuntu instaleld on the same PC. Do I have to install *Again* BF1942 via Wine in order to play it while I use Ubuntu? Or I can simply run it from it's windows installation without further issues?

---

### Post by GavinZac on 2007-12-19
> **peregrinogris said:**
> I would like to know if you can launch BF1942 directly from a windows installation using Wine. 
I mean, I have a WinXP and Ubuntu instaleld on the same PC. Do I have to install *Again* BF1942 via Wine in order to play it while I use Ubuntu? Or I can simply run it from it's windows installation without further issues?

No - your windows installation has a lot of stuff like dlls and registry entries that aren't accessible from within linux (this is partly why windows itself sucks so god damn much).

If you've still got windows installed and dont feel like installing BF again, just boot into windows. if you want to install BF in linux, why not delete windows to make room ;)

---

### Post by peregrinogris on 2007-12-20
> **GavinZac said:**
> No - your windows installation has a lot of stuff like dlls and registry entries that aren't accessible from within linux (this is partly why windows itself sucks so god damn much).

If you've still got windows installed and dont feel like installing BF again, just boot into windows. if you want to install BF in linux, why not delete windows to make room ;)

Argh! I supposed so. It's just that I'm a noob in this Linux thing :P That registry ¬_¬ The DLLs are somewhat modular, but the win registry is just a place where viruses and trojans can hide at pleasure :P But, I don't want to turn this in a Win vs. Lunux thread!

Thanks for the info. I think I'll have to install it again >_<

---

### Post by xzero1 on 2008-05-16
When trying to install battlefield 1942 I get "the folder %systemdrive% could not be created". I get this message immediately after selecting 'english' in the Choose setup language dialog box. I am using wine 1.0 +rc1 on a Hardy Heron AMD 64 computer.

---

### Post by Rickles65 on 2008-09-01
Thanks for the guide! First Windows game I've put on my system.

Any clues on why the fonts are garbled? When I start into the game the fonts are missing iterally the whole left half of each character.

The game itself doesn't display it's graphics properly, but I'm sure that's just playing with the ingame resolution settings.

TIA

---

