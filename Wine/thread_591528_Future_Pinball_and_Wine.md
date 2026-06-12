---
title: "Future Pinball and Wine"
date: 2007-10-25
forum: Wine
---

### Post by arigram on 2007-10-25
I managed to get Future Pinball working in Gutsy and Wine 0.9.47 but I still have some problems:

- Gamepad is recognized as Generic in the Options menu but it doesn't work in-game (Logitech ChillStream).
- FP sometimes doesn't open.
- Often doesn't open for a second time after been run once and closed.
- Sometimes hangs in the "compiling script" part of the table loading.
- Sometimes messes up the general display (Compiz runnning).

Apart from those problems, Future Pinball runs as well as in Windows with no visible performance or loading problems.

If someone can help me with the gamepad recognition, I would greatly appreciate it as one has much greater control and feel with the controller than the keyboard.

For those who don't know Future Pinball, they should take a look at:
[http://www.futurepinball.com/](http://www.futurepinball.com/)
[IMG]http://i184.photobucket.com/albums/x247/arigram/FuturePinballUbuntu.jpg[/IMG]

---

### Post by arigram on 2007-11-15
At the Future Pinball forums, LvR posted a script he made to help run FP on Wine and also instructions on its use.
With his permission, I cut and pasted the first post:

> This is a little guide for installing Future Pinball on Linux. I'll improve it with your remarks/questions/suggestions/etc...

FP runs on Linux with the help of Wine, which is an Open Source implementation of the Windows API on top of X, OpenGL, and Unix (see [http://www.winehq.org](http://www.winehq.org))

**Before Installing Future Pinball**

- You need a working linux installation.
I've done my tests on Ubuntu Feisty Fawn 7.04, but other disbtibution should work as well.

- You need a working 3D acceleration.
To check that your 3D acceleration is working, open a console and type :
Code:
glxinfo | grep direct

You should get :
```
direct rendering : Yes
```


- You need Wine to be installed.
Even if Wine is present in your distribution packages, I recommand you to install the lastest Wine from WineHQ Downloads
To check which version of Wine you have, type in a console :
```
wine --version
```

FP should work with Wine >= 0.9.40

Future Pinball installation with FPWine script

You can manually install FP, but it requires some Wine knowledges, so I've created a little script which does everything for you.
For more information see FPWine.
If you want to install it manually, see Future Pinball AppDb page.

Download the latest FPWine script into a fp directory (for example) and make it executable.
That can be done by typing following lines in a console:
```
mkdir fp
cd fp
wget [http://fprelease.free.fr/fpwine/latest/fpwine](http://fprelease.free.fr/fpwine/latest/fpwine)
chmod +x fpwine
```

You should now have fpwine script in a fp subdirectory in your home directory.
fpwine needs some others files, but it will automatically download missing ones.
If it fails, download manually and put in the same directory all missing files.

Now execute fpwine :
```
./fpwine
```

If everything goes ok, you can now run FP with the script ./runFP in the same directory, or with icons installed on your desktop and in your programs menu (Don't launch FP at the end of the setup as proposed).


As I've said before, I'll improve this guide and FPWine script if you have troubles or suggestions.
Maybe this guide could be set sticky ?

Now enjoy playing FP on Linux Wink

The original thread is at:
[http://www.futurepinball.com/forum/viewtopic.php?t=2713&postdays=0&postorder=asc&start=0](http://www.futurepinball.com/forum/viewtopic.php?t=2713&postdays=0&postorder=asc&start=0)
(need registration)

There are still some minor issues but he keeps working on it and he would certainly appreciate any help from you guys.

I would appreciate any help to get the gamepad working.

Future Pinball is a truly astonishing simulator of Pinball and a great free game that should be part of any gamers collection.

---

### Post by mjpatey on 2008-04-04
Hi,

Thanks for the great tutorial on how to get my pinball fix!  Everything seems fine up until I actually do ./runFP

When I do, the script returns the following error message:

kill: usage: kill [-s sigspec | -n signum | -sigspec] pid | jobspec ... or kill -l [sigspec]

Does the script need to change, or do I need a different version of "kill"?

-Mark

---

### Post by arigram on 2008-04-04
Btw, Future Pinball V1.8 was recently released and LvR also updated his script.

---

### Post by mjpatey on 2008-04-04
I just re-ran the new version of the script (which I think is the same one I ran before, but I'm not entirely sure).  I got the same results.

I'm running Gutsy, with Wine version 0.9.57.

Think I'll head over to the FP forums and ask the source!  Thanks for your help so far, though; I appreciate it.

-Mark

---

### Post by Xavier Oddmon on 2008-05-31
I did this once before on this machine with no problem, and I'm doing it again, but don't expect a problem. Something strange though: When I put ```
glxinfo | grep direct
``` into the terminal, compiz/metacity/everything graphical (x maybe) dies instantly, and I'm brought to the screen that you'd get if x isn't configured properly (running local boot scripts... etc) with no keyboard input. My graphics card is an ATI X2600HD.

---

### Post by hansonc01 on 2009-07-25
I think the FPWine script needs updating as i recieve this error...

can't download FuturePinballSetup_v1.9.20081225.exe

my guess is that that file is not longer at the location that the script thinks it is at.
In fact reading the other lines this is exactly whats going on.  I recieve a 404 error.  is there a new script available?

---

### Post by bakechad on 2009-07-26
> **hansonc01 said:**
> I think the FPWine script needs updating as i recieve this error...

can't download FuturePinballSetup_v1.9.20081225.exe

my guess is that that file is not longer at the location that the script thinks it is at.
In fact reading the other lines this is exactly whats going on.  I recieve a 404 error.  is there a new script available?

I recently used the FPWINE script to install it on Ubuntu 9.04.

Everything worked after I changed the Future Pinball location variable.

```
urlFP="http://members.iinet.net.au/~cleathley/downloads/FuturePinballSetup_v1.9.20081225.exe"
```


Try this change and it should work.

Let me know if you have any problems.

---

### Post by LADmaticCA on 2009-08-01
Thanks. That worked fine for me :).

---

### Post by bobuse on 2011-06-29
I've tried your installation script, but with my kubuntu natty, wineprefixcreate have been deprecated and doesn't exist anymore. So, you need to replace wineprefixcreate by wineboot, and installation seems ok.

---

