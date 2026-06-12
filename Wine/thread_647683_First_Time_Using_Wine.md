---
title: "First Time Using Wine"
date: 2007-12-22
forum: Wine
---

### Post by Het Irv on 2007-12-22
This is my first time using Wine and of course I am having some problems.  After dual booting for a while I decided to switch completely over to Ubuntu.  I only have one Windows program that I cannot use on another Computer, Sid Meier's Pirates.  The WineDB says that it will install but will not play, but these are old reviews and I was wondering if it worked under the new versions.  After some trial and error I cannot get the install to work.  I am having trouble with Mulitiple Disks.

---

### Post by Victormd on 2007-12-22
I want to totally migrate to Ubuntu but want to install some of my windows progz. I've heard (read) that Wine does the trick for most of them but I've never found a how-to... 
I guess this would help both me and Het Irv...

how do you use wine to install the quick and dirty way?
Thanks

---

### Post by cogadh on 2007-12-22
Quick and dirty?[LIST=1]
[*]Install the latest Wine. Follow the instructions [here](http://www.winehq.org/site/download-deb) to get the latest Wine.
[*]Open a terminal and run "winecfg" to set up your Wine directories and system settings. See the ["Stuff I've learned about Wine"](http://gaming.gwos.org/doku.php/wine:winestuff) link in my sig for some details on that.
[*]Put in your CD that you wish to install from and let it automount
[*]Close the file browser window and go back to the terminal. Type this to start the install:
```
wine /media/cdrom/<install executable>.exe
```
[*]Follow the prompts just like you would if you were installing in Windows.
[/LIST]
If you run into a problem swapping CDs, open a new terminal session and type "wine eject D:" to eject the CD and put in the new one (assuming that your CD drive is set up as "D:" in Wine). Let it automount again, close the browser window, then continue the install.

---

### Post by Het Irv on 2007-12-22
Wine is working now, but...not the program.  Audio is good, but the screen changes to 640 x 480 and turns black.  Is this the program not wanting to be Wined or Wine itself

---

### Post by cogadh on 2007-12-23
Probably the program not liking Wine, but it would be helpful to know what errors are produced by Wine in the terminal when you try to run the game. To get the terminal output, you need to use the terminal to run the game with Wine:
```
cd .wine/drive_c/Program\ Files/<game path>/
wine <game executable>.exe
```

Also, until you get it running, it might be helpful to turn on Wine's "Emulate virtual desktop" option. That will force the game to run in a Wine window, which will prevent it from affecting the desktop as a whole (also helps if the game locks up or crashes). You can find the virtual desktop setting in winecfg on the Graphics tab. Make sure you set the virtual desktop's resolution to a minimum of 800X600, anything smaller than that and some dialog buttons become inaccessible.

---

### Post by TolTime on 2007-12-23
what if you are just installing an executable file from the internet instead from a CD

---

### Post by cogadh on 2007-12-23
Then all you need to do is open a terminal, change directories to where you have the executable located, then "Wine" the executable:
```
cd /path/to/executable
wine <executable name>.exe
```

---

### Post by Victormd on 2007-12-29
Thanks Cogadh!
Worked like a charm... for now... hehehe

---

### Post by Victormd on 2008-01-09
> **cogadh said:**
> Quick and dirty?[LIST=1]
[*]Install the latest Wine. Follow the instructions [here](http://www.winehq.org/site/download-deb) to get the latest Wine.
[*]Open a terminal and run "winecfg" to set up your Wine directories and system settings. See the ["Stuff I've learned about Wine"](http://gaming.gwos.org/doku.php/wine:winestuff) link in my sig for some details on that.


I've installed Need for Speed Porsche Unleashed... the installation worked fine, now I'm getting an error related to DirectX, saying that I need DirectX 7 but have DirectX 0 (when wine is configured as windows nt/2000/xp) or says that I have DirectX 3 (when wine is configured as windows 95/98/Me). Any thoughts on this? Also, I looked at the link "Stuff I've learned about Wine" where it says not to install directx, so I'm a bit lost.

Also in this link, there is something about ALWAYS USE WINE UNINSTALL... well, then I'm screwed because I tried to uninstall NFS Porsche and get an error saying "The log file 'c:\Program Files\Electronic Arts\Need for Speed - Porshe Unleashed\Uninst.log' is not valid or the data has been corrupted. Uninstallation will not continue." How do I go about removing NFS?  Is there a "regedit" for Wine where I can delete the game directory and edit the registry to manually remove the game? :)

---

### Post by hikaricore on 2008-01-10
I just wanted to point out that Need For Speed Porsche Unleashed has a garbage rating on WINE's AppDB: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=2040](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2040)

---

### Post by Victormd on 2008-01-10
Thanks, I didn't notice that... Ok then... now how do I uninstall it? Simply delete the directory?
0 for 2!!!
Trying to install NFS High Stakes (received a Platinum ranking) and when I try to run the 3Dsetup, I get an "Error! Could not get 'HardWareKey' value." I click OK and try to run the game and "files are corrupt, re-install"...

---

