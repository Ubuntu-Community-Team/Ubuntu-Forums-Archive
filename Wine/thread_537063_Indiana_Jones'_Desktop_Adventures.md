---
title: "Indiana Jones' Desktop Adventures"
date: 2007-08-28
forum: Wine
---

### Post by Zalbor on 2007-08-28
This is an old Win3.x/Win95 game. It's gone abandonware now, and based on it being so simple I thought wine would be able to run it. Unfortunately, the installer doesn't even work and even if I install in windows and copy the files over to use with wine, it asks for a dll. And after copying that dll as well there are parts of the graphics missing.

The game (and a similar one called Yoda Stories) can be found [here](http://indysdesktop.googlepages.com/home2) if someone is interested. My question is, does anyone have an idea of how to get wine to run it?
My wine version is wine-0.9.44 (the latest deb from winehq).

---

### Post by cogadh on 2007-08-28
Is that one of LucasArts SCUMM-based games that can be run in ScummVM?

EDIT - I got it to install and run in Wine, but it has no sound, the game screen flickers and the install does produce an "could not create program group..." error. I had to extract the contents of the .zip file to a directory, then I used winecfg to create an entry for that directory under the Drives tab. I set the drive type to CD-ROM and then I set the Windows version to NT 4.0. I ran the install using "wine "F:\SETUP.EXE" and let it install in the default location. Then I cd'ed to that directory and ran the game using "wine DESKADV.EXE".

---

### Post by Zalbor on 2007-08-28
No, not related to scumm at all.

---

### Post by cogadh on 2007-08-28
OIC, I was editing while you were replying, check it out ^^

---

### Post by Zalbor on 2007-08-28
I did as you said and it installed, but the result is the same as when I "moved" the installation from windows. It's not just the flickering and the missing sound, some things are missing and the text doesn't appear. Thanks for the effort though! :)

---

### Post by plinydogg on 2008-04-05
If anyone can get the flickering problem to go away, I'd love to know how.

---

### Post by vinayg18 on 2011-06-07
Umm, bump?

---

### Post by plinydogg on 2011-06-07
Bump again. These games are super fun so it would be great if they would work better in WINE!

---

### Post by desktorp on 2011-06-08
Any updates on everyone's hardware/OS and Wine settings?

I'm assuming everyone has tried Wine's compatibility modes for Windows 9x, since it's the most obvious thing to present itself, but beyond that, what are you doing for sound?  What is the unspecified dll that was mentioned? Are you running it in a virtual desktop, fullscreen or neither?

Historically, Wine has had many audio problems, so my bet would almost always go toward the audio needing to be adjusted.  Try switching to ALSA if Pulseaudio isn't doing it for you, etc..  Unless someone runs in to the exact same problems as you, we'll probably need more info about your system + procedures, to be of any help.  I'm just stabbing in the dark with all this trashtalk about audio. 

Screen flickering could mean you do not have VSync enabled.

edit: a buddy of mine just reminded me that VSync can sometimes *cause* a program's graphics to flicker.. so just be sure to check for VSync and anything that mentions synchronizing graphics/sound/refresh rate..  :D :P

---

