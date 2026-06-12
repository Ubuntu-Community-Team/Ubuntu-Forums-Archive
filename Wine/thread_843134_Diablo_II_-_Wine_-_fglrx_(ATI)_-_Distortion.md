---
title: "Diablo II - Wine - fglrx (ATI) - Distortion"
date: 2008-06-28
forum: Wine
---

### Post by doomangel on 2008-06-28
I've been trying to get this solved for ages so now I'm gonna try asking :P

I'm using the latest fglrx from ATI, and I have a Radeon x1600.
I used wine to install diablo 2, and the installation went perfect, until I started the video test.

The screen gets distorted and split into two. I can't take a screenshot of this cause they seem to show up fine.

glxgears run fine without distortion, so I believe it's wine-related.

Since I couldn't get a screenshot, I took a photo of the screen.[IMG]http://i254.photobucket.com/albums/hh112/xarxex/DSC00113.jpg[/IMG]

---

### Post by mivo on 2008-06-28
Is it the same if you start the game without the video test? D2/LOD works flawlessly for me in Wine 1.0, but I have an Nvidia card, and skipped the video test.

---

### Post by doomangel on 2008-06-28
> **mivo said:**
> Is it the same if you start the game without the video test? D2/LOD works flawlessly for me in Wine 1.0, but I have an Nvidia card, and skipped the video test.

Yes, the same error appears ingame.

Edit: Could it be due to incorrect resolution? :S

---

### Post by mivo on 2008-06-28
My desktop resolution is 1680x1050, but when I start D2 in fullscreen mode, it switches to 800x600 (and back to 1680x1050 when I quit the game). Oh, and I currently don't have Compiz running (until a java bug is fixed, but that's a different issue), so you could try with metacity as window manager (type **metacity --replace &** in the terminal, or grab the Fusion Icon from the repository, package name is fusion-icon, which allows easy switching between the window managers). From my Windows days I remember there was a launcher parameter to run D2 in windowed mode. Google will probably yield some answers here -- that'd be my next step.

---

### Post by doomangel on 2008-06-28
> **mivo said:**
> My desktop resolution is 1680x1050, but when I start D2 in fullscreen mode, it switches to 800x600 (and back to 1680x1050 when I quit the game). Oh, and I currently don't have Compiz running (until a java bug is fixed, but that's a different issue), so you could try with metacity as window manager (type **metacity --replace &** in the terminal, or grab the Fusion Icon from the repository, package name is fusion-icon, which allows easy switching between the window managers). From my Windows days I remember there was a launcher parameter to run D2 in windowed mode. Google will probably yield some answers here -- that'd be my next step.

I don't run compiz (No need for fancy looks :P) so metacity is default, and running the windowed didn't help :(

---

### Post by terrax on 2008-06-28
> **doomangel said:**
> I've been trying to get this solved for ages so now I'm gonna try asking :P

I'm using the latest fglrx from ATI, and I have a Radeon x1600.
I used wine to install diablo 2, and the installation went perfect, until I started the video test.

The screen gets distorted and split into two. I can't take a screenshot of this cause they seem to show up fine.

glxgears run fine without distortion, so I believe it's wine-related.

Since I couldn't get a screenshot, I took a photo of the screen.[IMG]http://i254.photobucket.com/albums/hh112/xarxex/DSC00113.jpg[/IMG]

I can confirm this, and its very anoying.

Got a HD 3650.

This problem exist in native applikations also, such as Quake Wars. It happends when you change resolution in Quake Wars.

I went back to the older ATI driver, which works flawless.

BUT its not a wine, neither a kernel bug. Its a driver bug. I have tried 3 different kernels + a customized. Same same with all 3 kernels.

It does it in homeworld 2 with cedega and Quake WArs native applikation, and sure on other applications too, but didn't test it so much.

---

### Post by tatrefthekiller on 2008-06-28
I don't think it's wine related. It appends to me sometimes after a suspend to RAM, when the computer "wakes up". To fix it, I just ctrl-alt-backspace.

---

### Post by |{urse on 2008-06-28
> #!/bin/bash
metacity --replace &
sleep 2
wine /path/to/diablo.exe &&
sleep 2
compiz --replace &

wow.. ive posted this 3 times in a row on 3 seperate threads! :lolflag: Maybe that will help?

---

### Post by |{urse on 2008-06-28
> **doomangel said:**
> I don't run compiz (No need for fancy looks :P) so metacity is default, and running the windowed didn't help :(

srry im blind as well

---

### Post by doomangel on 2008-06-28
> **terrax said:**
> I can confirm this, and its very anoying.

Got a HD 3650.

This problem exist in native applikations also, such as Quake Wars. It happends when you change resolution in Quake Wars.

I went back to the older ATI driver, which works flawless.

BUT its not a wine, neither a kernel bug. Its a driver bug. I have tried 3 different kernels + a customized. Same same with all 3 kernels.

It does it in homeworld 2 with cedega and Quake WArs native applikation, and sure on other applications too, but didn't test it so much.

So, downgrading to an earlier version should fix it?

---

### Post by terrax on 2008-07-07
> **doomangel said:**
> So, downgrading to an earlier version should fix it?

Yep.. But the funny thing is, that after an reformat of my ubuntu, I run with newest catalyst witout a problem.

---

### Post by Dathokar on 2008-07-10
Hi !
I'm having the same problem with WoW on Wine.
I'm plying with a Radeon X1300 and the Catalyst 8.6 driver.
And I don't know what to do ...

Could anyone help me ?

---

### Post by cestabrook85 on 2008-07-11
It does seem to be an issue with the new ATI driver. I upgraded to 8.6 for the new UYVY and YUY2 pixel format support so I could use MythTV and now other apps that use 3D acceleration are distorted (not to mention MythTV).

The older driver that Ubuntu allows you to download seems to work much better.

Hopefully ATI fixes this in 8.7.

---

### Post by DoctorWho112 on 2008-07-12
the mythtv issue can be worked around by specifying a non-standard geometry when starting it. If your resolution is 1280x1024, you can try starting mythtv using ```
mythfrontend -geometry 1279x1024
```or```
mythfrontend -geometry 1279x1024+1+0
```It worked for me. I'm not too familiar with mythtv yet, maybe there is a config file where you can set this instead, so you won't need the command line everytime.

It is indeed a bug in the latest fglrx driver, and I would advise everyone with an older card (anything older than 4850/4870) to keep using the 8.5 fglrx drivers. However, the issue only appears to come up when using either Wine or MythTv, I haven't come across anything else that causes this corruption: full-screen OpenGL apps work fine, and I can watch full-screen movies without corruption.

So my advice is: handle with care. Don't upgrade unless you really need to.

---

### Post by unforeseen123 on 2009-05-14
I'm  having the same issue, but it's on start up.

Its the same in windows vista too!

BIOS, Kernal selection and boot  screens are fine. but as soon as the OS is loaded, the login screen goes mental like the picture you have.

I have an ATi 3650 1GB and an HPw20 monitor (running at 1650x1050 normally)


what is your hardware?

---

