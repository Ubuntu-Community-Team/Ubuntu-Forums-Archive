---
title: "WoW crashing and sound problems"
date: 2012-03-13
forum: Wine
---

### Post by ccolwell on 2012-03-13
Hello all im new to this forum and to Ubuntu I was hoping to get some help.  I've been trolling around and have tried just about everything i could find with searches.

I have a toshiba laptop L-35 s2151 with 1gb ram (2*512)
Ubuntu 11.1
new version wine

List of things ive done so far:

Installed wow using this guide:[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

regedit opengl key mod - made it worst 

configwtf: 
set gxApi "opengl" 
set ffxdeath "0"
set ffxGlow "0"
set soundoutput system "1"
set soundbuffer size "150"



uninstalled fglrx / uninstalled open source video driver (ati xpress 200m) then reinstalled fresh using tutorial i found somewhere here.

did steps 1-10 for sound problem [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)
log for alsa info-  [ATTACH]214236[/ATTACH]

K now the problems I got the game running tolerable with implementing these mods one at a time to see if improved.  

Sound works then gets a lil garbled then cuts off if i go to in-game menu and adjust sound quality sometimes it resets and starts working again but not for long.  

video will start to seem like im lagging then go Link dead and kick up this error - [ATTACH]214235[/ATTACH] 

the game freezes and i usually have to do a hard reboot because i cant get out of game mode

Thank you for your time ...............Cliff

---

### Post by ccolwell on 2012-03-13
**tried this too second part. there wasnt any selections for these though. Check both ALSA and OSS.  Be sure "Hardware Acceleration" is set to "Full", and that "Driver  Emulation" is unchecked.**

[B]
[/B]

**No Sound or other unrelated issues**

 To fix sound, or possibly other problems, first try adding 
SET ffxDeath "0" SET ffxGlow "0" to  "/home/<username>/.wine/drive_c/Program Files/World of  Warcraft/WTF/Config.wtf", without the quotes, where <username> is  you computer login name. Try to run World of Warcraft. If this doesn't  work, remove the text, and type in  
winecfg into  a terminal. Click add application. Select C:\Program Files\World of  Warcraft\Wow.exe or where ever your Wow.exe file is. Highlight Wow.exe.  Select "Windows 2000". Then go to the Graphics tab. Uncheck "Allow  window manager to control the windows" and "Allow window manager to  decorate the windows". Now go to the Audio tab. Check both ALSA and OSS.  Be sure "Hardware Acceleration" is set to "Full", and that "Driver  Emulation" is unchecked. Now go to the "Drives" tab. Press  "Autodetect..." Now press "Apply" and then "Ok". Now start World of  Warcraft. Exit at the log-in screen. Now type  
winecfg into  a terminal again. Go to the "Graphics" tab. Recheck "Allow window  manager to control the windows" and "Allow window manager to decorate  the windows". Press "Apply", and then "Ok". It should now work  perfectly. Try the graphics tweaks for added effect on performance!

---

### Post by cwwilson721 on 2012-03-13
Punctuation.
Formatting.
It helps makes things readable.

---

### Post by ergo-proxy on 2012-03-16
To get sound working choose exact values instead of default in audio tab

---

