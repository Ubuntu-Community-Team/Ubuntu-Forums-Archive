---
title: "Steam only letting me use DirectX 8.1"
date: 2007-11-17
forum: Wine
---

### Post by sneezweasel on 2007-11-17
I installed Ubuntu last week and I'm a total noob to it

I'm running a 2.66 dual core Intel processor and an GeForce 8600GTS with 4 gigs of ram on gutsy. 

I installed steam and portal through Crossover and it went very smoothly. I open up portal, that also runs fine. except that it is running in DirectX 8.1 with no anti-aliasing. Do I need to install DirectX 9 somehow or what?

Thanks


EDIT: It says software DX level is 9.0, but hardware is 8.1 in the video options.

---

### Post by Goneval on 2007-12-04
The same thing happens to me.

the only "tiny" difference is that **I am running Windows XP Pro**.

Therefore I think the **problem is Steam or Portal** _not_ Crossover or ubuntu.

I hate **Direct X 8.1** because its optimized for old computers and it lags and the portals looks boring with Direct X 8.1


EDIT: Just as you know:
I have installed the latest Direct X 9.0c for Windows XP

---

### Post by bastiegast on 2007-12-04
The solution is:
First of all:  USE WINE, please!
Crossover is good, and you're supporting wine by using it but for games using just wine really works better.
If you install the latest wine(see the site for instructions, it only involves adding a repo and update) you will be able to run portal and in dxlevel 9.0. For me there was one drawback and that's that performance was very bad on my amd 64 300 + GF 6800 system that should theoretically be able to handle it. Maybe its better on your system. 
You ask just at right moment because a few days ago, when wine 0.9.50 was not yet released, dxlevel 9 caused graphical corruptions. That's fixed now.

---

### Post by cogadh on 2007-12-04
> **Goneval said:**
> The same thing happens to me.

the only "tiny" difference is that **I am running Windows XP Pro**.

Therefore I think the **problem is Steam or Portal** _not_ Crossover or ubuntu.

I hate **Direct X 8.1** because its optimized for old computers and it lags and the portals looks boring with Direct X 8.1


EDIT: Just as you know:
I have installed the latest Direct X 9.0c for Windows XP
Actually, if you are using the game in Windows XP and it only lets you use DX 8.1, then chances are your hardware is not DX 9 compliant. It has nothing to do with Steam or Portal working incorrectly, they automatically detect the correct DX level for your hardware and force that version. They only way you will get the game to run properly at DX 9 levels is to upgrade your hardware to a fully DX 9 compliant device.

In Wine/CrossOver/Cedega, it's a different story. Since Wine doesn't have Windows drivers and hardware detection is not perfect, the automatic DX detection built into Source games defaults to DX 8.1, even if your hardware is DX 9 compliant.

In order to make the game run with DX 9, you need to tell it to force the DX level by adding "-dxlevel 90" to the game's launch parameters in Steam or in the command path you use to launch the game.

---

### Post by bastiegast on 2007-12-04
> **cogadh said:**
> Actually, if you are using the game in Windows XP and it only lets you use DX 8.1, then chances are your hardware is not DX 9 compliant. It has nothing to do with Steam or Portal working incorrectly, they automatically detect the correct DX level for your hardware and force that version. They only way you will get the game to run properly at DX 9 levels is to upgrade your hardware to a fully DX 9 compliant device.

In Wine/CrossOver/Cedega, it's a different story. Since Wine doesn't have Windows drivers and hardware detection is not perfect, the automatic DX detection built into Source games defaults to DX 8.1, even if your hardware is DX 9 compliant.

In order to make the game run with DX 9, you need to tell it to force the DX level by adding "-dxlevel 90" to the game's launch parameters in Steam or in the command path you use to launch the game.

And actually wine 0.9.50 is the ONLY piece of software that lets you run portal in dxlevel 90 without graphical corruption(at least the green textures where gone, I couldn't test more because performance sucked)

---

### Post by Goneval on 2007-12-05
> cogadh: 
Actually, if you are using the game in Windows XP and it only lets you use DX 8.1, then chances are your hardware is not DX 9 compliant.

I have the Laptop version of ATI X1600.

I played Portal with Direct X 9 before it got messed up.

But lets not talk about Windows.

EDIT:
I added " -dxlevel 90" and launched it. Now it works the Hardware and Software runs DX9
Thanks cogadh

---

### Post by ebichu on 2007-12-05
also, before playing you should configure your wine, eg in registry put your video card's memory size and such. source games will run better. at least they did on my machine.

---

### Post by faheyd on 2008-01-26
> **ebichu said:**
> also, before playing you should configure your wine, eg in registry put your video card's memory size and such. source games will run better. at least they did on my machine.

Hi all,
 I've installed wine-0.9.54 on 7.10.  Steam client works fine now that I've gotten the gecko thing fixed.

However, in the Steam client, when I click on CounterStrike Source game, I get a little window that says, 'Steam - The latest version of DirectX is required' and it won't let the game start.

I get this error in spite of whatever '-dxlevel XX' I put in the command line or start up options.

Any help?  TIA

---

### Post by DAaaMan64 on 2008-01-29
I am getting the same error, anyone find anything out yet?

thank you.  This is the latest wine btw

---

### Post by DAaaMan64 on 2008-02-05
No one knows ANYTHING about this?  I can't find it in the WineHQ.  Does someone have something?

thank you. :)

---

### Post by faheyd on 2008-02-06
> **DAaaMan64 said:**
> No one knows ANYTHING about this?  I can't find it in the WineHQ.  Does someone have something?

thank you. :)

I've opened up a Bug 11487 on the winehq site, I have no idea if I did it right, but we'll see. ] (*,)

---

### Post by faheyd on 2008-02-06
> **DAaaMan64 said:**
> No one knows ANYTHING about this?  I can't find it in the WineHQ.  Does someone have something?

thank you. :)

OK, here's the story:

Reinstalling wine worked.  Also the 'install gecko' worked also.

On the original install, I did not 'wait' for the over 5 minute installation of
'winecfg' to work.  I just renamed the wine.xxxx to wine and went from there.
A big mistake.  


(copy Steam to another directory for safe keeping)
1.  Removed .wine via cd home directory,  rm -rf .wine
2.  Full Removal of package via Synaptics
3.  Reinstalled via Synaptics (must have new repo's in config for latest wine)  [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)
4.  Open terminal, cd home directory, run 'winecfg', see multiple errors with
mixer/printer, etc, IGNORE.
5.  Take coffee break, come back 10 minutes later
6.  Wine installed
7.  Moved my Steam directory back into Program Files.
8.  cd to Steam, run wine ./Steam.exe
9.  Steam opens up, asks for Gecko install, say yes
10. All is well, can't seem to keep video settings, but I'll work that out.


For Vitaliy Margolen/WINE, Thanks for the help with my noob mistakes .
I closed the BUG report.

---

