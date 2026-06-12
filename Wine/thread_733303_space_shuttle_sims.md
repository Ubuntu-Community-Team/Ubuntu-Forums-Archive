---
title: "space shuttle sims"
date: 2008-03-23
forum: Wine
---

### Post by pibb69173 on 2008-03-23
im looking for a game that puts u in the cockpit of a space shuttle and you launch into space from earth that either runs nativly on linux or throu wine it dosent have to have super graphics [and not vegastrike]

---

### Post by jessika-kaos on 2008-03-23
I dunno if Orbiter would work with wine or not.  You could try it.

[URL="http://orbit.medphys.ucl.ac.uk/"]
http://orbit.medphys.ucl.ac.uk/[/URL]

---

### Post by pibb69173 on 2008-03-23
i tried it the mission setup works but when i press play nothing happens

---

### Post by pibb69173 on 2008-03-23
i have wine fix installed and i tried it it started i pressed play it starts to load then crashes

---

### Post by Shazaam on 2008-03-24
Per the Orbiter wiki......

Does Orbiter run under Linux?
Not on its own. It is designed and compiled especially for Windows. There are currently no plans to port Orbiter to Linux. As additional trouble, the Orbiter SDK is especially designed for Windows, making all addons limited to a Windows environment, as well.

It is also currently not possible to run Orbiter under a Windows emulator like "Wine", because of DirectX (but this might change if technology advances).

It IS possible however to use VMware Player to emulate Windows, and run Orbiter that way. Unfortunately, this is only possible if you already have a Windows license. 

[http://www.orbiterwiki.org/wiki/FAQ](http://www.orbiterwiki.org/wiki/FAQ)

---

### Post by pibb69173 on 2008-03-24
thanx/ windows licence?

---

### Post by nalmeth on 2008-03-24
I'm sure someone can correct me if I'm wrong, but I don't think you can run anything 3D in a virtual machine. 
AFAIK that option is not possible

I would guess that getting it to work with wine is the best option, and a difficult one at that
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=2269](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2269)

---

### Post by pibb69173 on 2008-03-24
is there a toturial cause no one says what 2 do to make it run

---

### Post by pibb69173 on 2008-03-25
soo if any one ever got this to work it would be aprecated if u wrote a how to or a toturial, lookin foward to that, thanx

---

### Post by happyhamster on 2008-03-25
I sort of got it working (it's slow though). Settings: Ubuntu Hardy Heron beta, wine 0.9.58, Nvidia 169.12 driver (7300GT video card).

- First I installed VC++ 6 using the winetricks script. Get the script here:
[http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

- Navigate to where you downloaded the script:
cd /path/to/where/you/downloaded/the/script

- Make the script executable:
chmod +x winetricks

- Run winetricks to install vc6:
./winetricks vcrun6

- Configure the wine registry: create an empty text file (using gedit for example) and copy&paste:
> 
[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"DirectDrawRenderer"="opengl"
"VideoMemorySize"="256"
"UseGLSL"="enabled"
"OffscreenRenderingMode"="fbo"
"RenderTargetLockMode"="readtex"

- Save the file as "orbiter.reg". Then from the same folder as that file, run:

wine regedit orbiter.reg

- Next, from within the orbiter folder, run wine like this to start:

WINEDEBUG=-all WINEDLLOVERRIDES="msvcirt=n" wine orbiter.exe

It looks pretty good, but it's slow, and I have no sound (but that may be because my config is pretty messed up at the moment).

---

### Post by pibb69173 on 2008-03-26
i really preciate ur post and yes it runs but since my comp is old : Dell Dimension 4300, 512mb ram, ATI rage 128 Pro Ultra TF vid card: its hard to play

---

### Post by kostkon on 2008-03-31
What's more realistic than the classic Space Shuttle simulator game called simply *Shuttle*. Believe me, it's the best! It will run just fine on your PC with *DOSBox*, just increase the CPU cycles a little.

You will find it on sites that offer downloads of old DOS games.

---

