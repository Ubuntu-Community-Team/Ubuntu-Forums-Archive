---
title: "run program for windows (wine?)"
date: 2013-01-15
forum: Wine
---

### Post by marchelloUA on 2013-01-15
Hi all, 

how do I run program for windows? Should I use wine? Actually, I have never tried it, so the word "wine" is all I know. Some example will be appreciated.

---

### Post by slickymaster on 2013-01-15
You can either use [Wine]("http://www.winehq.org/") (to simulate the Windows environment) to run your Windows applications in Linux or you can ran Windows in a Virtual Machine in Linux with [VirtualBox]("https://www.virtualbox.org/").

One other way is to run Windows applications on a remote Windows system and control it from your local system, using terminal services, which runs on a Windows server, like [rdesktop]("http://www.rdesktop.org/"), [Citrix]("www.citrix.com/") or [Propalms]("http://www.propalms.com/").

---

### Post by howefield on 2013-01-15
You might want to look at Linux alternatives before running Windows programs through wine. (Perhaps you have done and there are none that you find acceptable). Just saying.

Wine is terrific at what it does and for the applications which run well can be an extremely useful tool.

---

### Post by marchelloUA on 2013-01-15
[[COLOR=#DD4814]**howefield**[/COLOR]]("http://ubuntuforums.org/member.php?u=186490"), 

yea, I tried to look for Linux alternatives and will go on searching. 

Could someone please give me example of installing wine and running some windows program ?

---

### Post by slickymaster on 2013-01-15
You can install Wine via Software Center (Ubuntu's default repository includes Wine), Synaptic Package Manager (if you have it), or via terminal:
```
sudo apt-get update && sudo apt-get install wine
```

---

### Post by squakie on 2013-01-15
You can also try playonlinux - it's sort of a front end to wine.  There is also a non-free product called CrossOver - I have used that with success on what I've needed.  Both the winehq site and the crossover site have list of programs that work and to what degree they work.

If you are planning on playing a Windows game, then I would suggest you use a dual boot so you can truely boot Windows when you want to play the game.  I say this because there is a perfomance hit when running in wine, and a virtual machine will not provide the graphics you probably would want for the game.  These things are constantly evolving, so don't be afraid to just try wine and/or try a virtual machine and see if they perform the way you need them to.

---

### Post by Toz on 2013-01-15
This site is a good resource: [http://appdb.winehq.org/]("http://appdb.winehq.org/"). Search for the application you want to run - you may get some more information about installing and running the application posted by others who have tried.

Moving this thread to the Wine section of the forum.

---

### Post by mastablasta on 2013-01-15
> **squakie said:**
>  I say this because there is a perfomance hit when running in wine, ...
 
that's true but sometimes performance in wine can be better than under windows.
 
play on linux will make it easier for newcommers to configure the programme and it also comes with some preconfigured options for certian programmes. for some these work well for some not so good. 
 
anyway it's not so difficult to use wine. thoguh knowing osme windows/dos command line would come in handy.
 
if you post the programme you want to run maybe someone here can help you. maybe someone already made it run.

---

