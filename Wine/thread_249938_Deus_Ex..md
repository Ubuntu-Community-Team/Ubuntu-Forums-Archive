---
title: "Deus Ex."
date: 2006-09-03
forum: Wine
---

### Post by BoomAM on 2006-09-03
Hi.
Im relativly new to getting windows apps working on Ubuntu, so if anyone can help with this, it'll be much appriciated :):

Is there a way to get Deus Ex running under Ubuntu?
I asume i'd have to use WineX?
Any guides around?

Thanks in advance all. :)

---

### Post by wylfing on 2006-09-03
Supposedly Deus Ex should work fine, but that has not been my experience. Of course, a while back my young son got ahold of my disc so it's not in the best shape, and that might be the source of my problems.

You'll need to get Cedega if you want to play most Windows games under Linux. Wine itself works for a few games, but performance and graphics tend to be worse than with Cedega. The downside to Cedega is you have to pay $15 for it, but mainly it's a 1-time investment and in my opinion it's worth it.

After you get Cedega installed, there should be nice, friendly selections on your applications menu from which you can install and run games.

---

### Post by dbd on 2006-09-03
With Deus Ex  you should be ok just with wine, so you don't need to buy Cedega wineX. There should be plenty of info on wine here:
[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

And if you have problems check out the info on getting Deus Ex to work here:
[http://appdb.winehq.org/appview.php?iAppId=186](http://appdb.winehq.org/appview.php?iAppId=186)

Good luck :)

---

### Post by BoomAM on 2006-09-03
Thanks for the links guys/gals.
I'll give it at try tomorrow.
I'll report back if i have problems.  :)

---

### Post by Anakashar on 2006-09-03
I have Deus Ex loaded on my Kubuntu machine, running just fine and full-speed (with maybe a little slowdown maybe from the OpenGL drivers).

I used the loki installer.  [http://liflg.org/](http://liflg.org/)

That sets it up to work just fine.

---

### Post by BoomAM on 2006-09-09
Ive tryed that Loki installer, and it installs, but it doesnt work?

Ideas?

---

### Post by BoomAM on 2006-09-09
The error i get is that Deus Ex, when i run it with 'wine deusex.exe', is that it keeps asking for the CD, when its in the drive?

---

### Post by ZylGadis on 2006-09-09
To run anything (that performs a cd check) with wine, you need a no-cd crack - it is legal to use one if you own the game. Deus Ex runs fine. Check people's experiences with it at [http://appdb.winehq.org](http://appdb.winehq.org)
Also, a user above reports that Cedega runs more games than wine. That is simply not true, and you can get that information by comparing Transgaming's database with wine's one. What is more, Transgaming defy everything that linux is, and every person who is aware of linux's ideals and upholds them should avoid Cedega.

---

### Post by BoomAM on 2006-09-10
> **ZylGadis said:**
> To run anything (that performs a cd check) with wine, you need a no-cd crack - it is legal to use one if you own the game. Deus Ex runs fine. Check people's experiences with it at [http://appdb.winehq.org](http://appdb.winehq.org)
Also, a user above reports that Cedega runs more games than wine. That is simply not true, and you can get that information by comparing Transgaming's database with wine's one. What is more, Transgaming defy everything that linux is, and every person who is aware of linux's ideals and upholds them should avoid Cedega.
I only plan on using Wine to run DX1 tbh. :p
Im not paying for a service to play games when i can simply use Wine, or if it doesnt work, reboot and use Windows. :p

Ive tryed a few no-cd patches, but none seem to work?

---

### Post by dbd on 2006-09-10
Are you still getting missing CD errors with the no cd cracks?

Are you sure they are for the version you are using, it might be worth patching the game and then trying to install the cracks again.

---

### Post by BoomAM on 2006-09-10
I found a way around it.
I copyed my DX install from my windows PC to it, and then tryed, and it worked.

The problem im having now is that the mouse control had a 2-3 second delay and everythings jerky.

---

### Post by NMUrugbysteve on 2006-09-11
You should make sure that your rendering device is set to opengl. Just go into the main menu and "display." Then you should get a menu that just says direct3d or software rendering, you're going to want to click the "unsupported devices" and pick opengl.

---

### Post by BoomAM on 2006-09-12
I already did that.
Still happens.

---

### Post by benhall on 2006-09-12
You might have done this, but you need to make sure that you have a wine drive linking to your cdrom- this can be done with winecfg, under the drives tab. Some games need to see that a CDROM exists before they can be played. I can run Deus Ex, with DirectX rendering, without any issues on my Ubuntu and Mandriva boxes, without a CD crack. Some typical things worth checking if you have problems are 
*Choice of sound drivers/acceleration (set to emulation if in doubt)
*Try running in a virtual desktop (I need to this for Ubuntu, but not mandriva- this is probably a hardware thing)
*Try the stock ubuntu version of wine- there have been a lot of changes in wine directx recently and some regressions might have appeared
Good luck!

---

### Post by BoomAM on 2006-09-12
> *Choice of sound drivers/acceleration (set to emulation if in doubt)
How?

> *Try running in a virtual desktop (I need to this for Ubuntu, but not mandriva- this is probably a hardware thing)
How?
& Wont that make it run worse?

> *Try the stock ubuntu version of wine- there have been a lot of changes in wine directx recently and some regressions might have appeared
How do i find out what version im running, im just using the one out of the repositories.

---

### Post by benhall on 2006-09-13
To change the graphics and sound options, use winecfg (type it from the prompt) and look at the respective tabs. For DE I use OSS, as I have had problems with stuttering sound in Jedi Outcast with ALSA. That said, using ALSA gives me the best sound running Morrowind (FYI this requires a patched wine). To set the hardware acceleration to emulation, look at the drop down box at the bottom of the screen.
I set the graphics to use a virtual window as otherwise wine doesn't use the full screen properly. In particular it doesn't get the correct resolution and positions the graphics inappropriately. Your milage may vary though- on an older Mandriva box I have I can run it fullscreen without issue. Whether it makes it run worse, you will have to see. I have no technical difficulties running it in a window (in terms of smoothness)- but thats not to say that it will be true on all hardware of all ages. Several other games seem to need a windowed enviroment on this particular box for me, but if you look in the appdb you can find some programs that prefer a windowed environment irrespective of the box.
The version you are using will depend on whether you have added the wine ubuntu repository- if you haven't then I don't think that there should be a problem arising from the version. Alternatively to get the version type "wine --version" at the prompt.

---

### Post by mlind on 2006-09-13
Deus Ex is probably one of the best games ever made, thanks for reminding me about this gem. :KS  
Now I just need to find that damn cd..

---

### Post by jetsetlemming on 2006-09-14
I don't know how this might work with Ubuntu, since I'm quite new to it, but I'd imagine the installation would have the same files, since you're fooling it into thinking it's in windows anyway, right? 
Since I'm not at all sure how even the file system works in ubuntu, I'm going to give these directions as if we were talking about windows, and you can translate. ;P 
How to run Deusex without the CD:
Open up the Deus ex folder, and go into the system folder. Find the deusex.ini file, and open it with a word processor/document type program (what's ubuntu's version of notepad?). This file holds all of Deus Ex's settings and directions. Under the area "[Engine.Engine]", the last line reads "CdPath=_." where the blank is your CD drive letter. Delete the drive letter (So it's "CDPath="), or erase the entire line. This prevents DX from checking for a CD at all. ^_^

---

### Post by Schapie123 on 2006-09-14
I have one problem with Deus Ex. On my system it seems to run in hypermode! Is there any way to make the game run at the speed it is supposed to?
I use the opengl mode, and have the latest version of wine installed through their repository.

---

### Post by BoomAM on 2006-09-14
> **Schapie123 said:**
> I have one problem with Deus Ex. On my system it seems to run in hypermode! Is there any way to make the game run at the speed it is supposed to?
I use the opengl mode, and have the latest version of wine installed through their repository.
I dont think that thats an Ubuntu/Wine problem, as the same happens on my XP machine with DeusEx as well.
Quite handy in parts, as i can blaze through the early bits mega-fast. :p.

---

### Post by DeVelaine on 2006-09-21
I got it running relatively quickly last Sunday. It was my project for the day as part of my transition away from Windows (I might never be able to fully do that until Adobe/Macromedia gets off their collective rear and finally allows Linux users to have the most recent version of the Flash drivers). However, I'm currently encountering a slight graphic glitch, manifesting itself in two locations.

Most characters appear to have either clear or pink "visors" for lack of a better word over their eyes. I've seen this once in Windows, but it wasn't on the character in the next map, so I ignored it. The other issue is with certain weapons (shotgun, 10mm pistol, assault rifle, assault shotgun, and PS20 as far as I know), there is a "panel" and a "cone" placed at the barrel of the weapon, almost as if it's representative of a muzzle flash.

Is this an issue with the nVidia drivers, or just the OpenGL support?

---

### Post by ctgray on 2006-09-22
Those problems happened when I was running Deus Ex in Windows so it's not a Linux specific problem. I can't remember what I did to get rid of it.... I think I just re-installed and re-patched from memory (couple of years ago).

---

### Post by DeVelaine on 2006-09-23
> **ctgray said:**
> Those problems happened when I was running Deus Ex in Windows so it's not a Linux specific problem. I can't remember what I did to get rid of it.... I think I just re-installed and re-patched from memory (couple of years ago).

Actually, I was just playing around with it in Windows, after getting the 1112fm patch installed, and that error is in Windows. I find that odd now.

---

### Post by DeVelaine on 2006-09-25
Complete reinstall and upgrade to 1112fm hasn't solved the problem. Nor has an upgrade to the latest nVidia drivers. However, now I can't boot into my Windows partition. I highly doubt it's related, but I still find it amusing.

---

### Post by SneakyMonkey on 2006-10-30
> **Schapie123 said:**
> I have one problem with Deus Ex. On my system it seems to run in hypermode! Is there any way to make the game run at the speed it is supposed to?
I use the opengl mode, and have the latest version of wine installed through their repository.

I too am have encountered this problem. Everything else works great and after doing a little research I found that some people solve this problem by playing the game with compatibility mode in windows XP. I set the DeusEx.exe to run using Windows 95 in the winecfg but that doesn't seem to work either. I wonder if anyone else has discovered any way to fix this problem.

---

### Post by SneakyMonkey on 2007-01-12
> **SneakyMonkey said:**
> I too am have encountered this problem. Everything else works great and after doing a little research I found that some people solve this problem by playing the game with compatibility mode in windows XP. I set the DeusEx.exe to run using Windows 95 in the winecfg but that doesn't seem to work either. I wonder if anyone else has discovered any way to fix this problem.

I have fixed my own problem and I hope this solution can aid anyone else who is having the same problem. First I narrowed it down to the fact that when the game starts it takes a reading of you initial CPU speed, because I had AMD Cool'n Quiet Enabled in my BIOS my CPU would slow down when not being used. So when the game started up the computer would see a CPU running at 1 GHz instead of 1.8 GHz then my computer would over compensate resulting in the game running too fast. So to solve the problem I went into my BIOS and turned of AMD Cool'n Quiet. Now I can finally enjoy Deus Ex in all of it's full, normal speed, glory.

---

### Post by KhaaL on 2007-12-14
Is it possible to change the speed from within ubuntu? I don't have anything on Speedstep or cool'n'quiet in my BIOS... By the way, I also am on a AMD X2 5000+, should I disable the game from using both cores? (and in that case, how?)

---

### Post by BoomAM on 2007-12-17
Should be fine running both cores. 
Its not a SMP game, so what would happen is that Ubuntu would just use the other core for other tasks.
If what SneakyMonkey said is true, then just turn off any processor throttling you have in your BIOS (either C&Q or SpeedStep).
:).

---

### Post by Saturnina on 2008-09-13
Has anyone else encountered a problem on the first time running Deus Ex when it tries to find the 3d devices? The program just hangs in that window. I've tried editing the deusex.ini file but I can't seem to bypass that first run window to test if the problem is the window or something else entirely. When testing the OpenGL driver, everything seemed to work fine, so I don't know why Deus Ex can't recognize it.

---

### Post by jim_24601 on 2008-09-15
The Deus Ex running at warp speed problem is caused by CPU frequency scaling, yes. See [this post]("http://ubuntuforums.org/showthread.php?t=739621"). You can turn it off from within Ubuntu using
```
sudo /etc/init.d/powernowd stop

```
and back on with
```
sudo /etc/init.d/powernowd start
```

---

### Post by huzy on 2008-11-27
Hello to everyone. 
This is my first post as i am a brand new convert to ubuntu...I've installed Deus Ex using wine no problem, but the problem im having is that everytime i start deus ex, it runs the first time setup to select graphics options etc. The problem i have is that it seems to 'freeze' when i get to the screen for choosing my graphics card options. Nothing appears for me to select and nothing ever happens after a while. 

im running a toshiba satellite m60 with a Intel Centrino 1.7 with a ati x600se. 

Any help/suggestions?

Huzy

---

### Post by Progressive on 2008-11-27
You need to use the OpenGL renderer as described here:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3775](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3775)

I recommend following all the instructions there so you can get the latest updates and the new HDTP texture overhaul.

---

### Post by jony121 on 2011-11-20
> **Anakashar said:**
> I have Deus Ex loaded on my Kubuntu machine, running just fine and full-speed (with maybe a little slowdown maybe from the OpenGL drivers).

I used the loki installer.  [http://liflg.org/](http://liflg.org/)

That sets it up to work just fine.

Does anyone still have this installer?

deus.ex_1112fm-english.goty.run

---

### Post by sffvba[e0rt on 2011-11-20
Back to sleep thread...


404

---

