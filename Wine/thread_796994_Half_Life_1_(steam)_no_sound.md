---
title: "Half Life 1 (steam) no sound"
date: 2008-05-16
forum: Wine
---

### Post by OpposingForce on 2008-05-16
[CENTER][SIZE="5"]**Solved:**[/SIZE][/CENTER]

Hey everyone, I just installed Steam through WINE and it seems to have worked well.  I installed Half Life and went to play it.  Now I can hear sound in the menus (like when I click new game I can hear the little menu sounds).  But when I get in game I don't hear anything.  I have WINE set up to use OSS drivers (I have OSS4 because its the only thing that supports my Creative XFI card) if anyone could help that would be great.

**Issue Solved:**

Had to check "driver emulation" in the audio tab of wine's configuration box.

---

### Post by OpposingForce on 2008-05-16
Also just installed and tested Counter Strike 1.6.  I'm getting no sound, even in the menus, and no servers are showing in the games list.

---

### Post by OpposingForce on 2008-05-17
Update: Just installed and tried Team Fortress 2 (source engine game) and it won't even start.  Says something about my card not supporting pixel shader 1.1 .. which is odd because I have a nvidia 6800 which supports SM 3.0 and I also have the linux drivers for the card and have wine set to use pixel shaders.

---

### Post by Rhubarb on 2008-05-17
If it's of any help, I've got wine 1.0 rc 1 running portal + steam here no problems on my 64bit ubuntu 8.04 install.

You may possibly be missing a pulse audio progam (do a search in synaptic for pulse audio - it may be one of those).
This fixed up a no-sound issue I was having with some SDL sound based games.

---

### Post by OpposingForce on 2008-05-17
thanks for the response, I seem to have pulse audio installed (according to the green filled box in synaptic) is there a specific file that I should try?

---

### Post by Rhubarb on 2008-05-17
> **OpposingForce said:**
> thanks for the response, I seem to have pulse audio installed (according to the green filled box in synaptic) is there a specific file that I should try?
To be honest I can't quite remember which one, I do know that in winecfg I told wine to use alsa rather than oss for sound.

---

### Post by OpposingForce on 2008-05-18
Unfortunately ALSA isn't going to work for me, I use OSS4 because it has Creative Xfi support, I don't have any other choice if I want to hear sound on my computer in linux.  Also still having that problem with TF2 if anyone can help.

---

### Post by OpposingForce on 2008-05-20
The issues still persist, and I also noticed HL1 runs quite choppy in addition to having no sound in game (sound works in main menu but not in game). My computer can (in windows xp) play HL2 on high settings perfectly fine, so there's no reason why I should be getting such horrendous performance in a game that's over 10 years old.

Again, I'm running a Nvidia 6800 GT, drivers are installed and I checked "Hardware Drivers" and they are listed there and shown as "enabled".  Steam must not be detecting these drivers somehow.

---

### Post by OpposingForce on 2008-05-20
Someone on another forum helped me get tf2/source games working, he wrote the guide for gmod but it helped me get TF2 working, should work for all source games.  I think in the 1.0 rc-1 version of wine friends is fixed so you might not have to disable friends.  

[QUOTE=philxyz]1) Install wine (version 0.9.60 works best for me at the moment, 0.9.61 was broken when I tried it).
2) Save this file to your Desktop: [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
3) Open a terminal and "cd" to your Desktop
4) The lines with the dollar sign below: type the text after it into your terminal:

$ ./winetricks gecko
(this installs the web renderer to display the steam store)

$ regedit
(you know what this does if you've used windows before)

Inside regedit, navigate to:
HKEY_CURRENT_USER/Software/Wine/
Right click on the "Wine" key (looks like a folder) -->
Select "New Key" and name it "Direct3D"

Right click on the "Direct3D" key -->
new string called "OffScreenRenderingMode", right click it, click Modify and enter "backbuffer"
new string called "UseGLSL", right click it, click Modify and enter "disabled"
new string called "VideoMemorySize", right click it, click Modify and enter "256" or whatever your graphics card RAM size is in MB.

Exit regedit

Change into your steam directory:
$ cd ~/.wine/drive_c/Program\ Files/Steam

run steam using:
$ WINEDEBUG=-all wine Steam.exe

In Steam:
View -> Friends -> Status -> Set to "Offline" (steam friends is still screwy but due to be fixed before wine 1.0)

Also in Steam:
File -> Settings -> In Game -> Uncheck "Enable Steam Community in game" (otherwise it causes the game to crash before you even see the guy with the cone on his head)

Right click on the source game you want to play in the steam games list
enter the following startup commands:
-width 1280 -height 1024 -dxlevel 95

^ make sure to use the right settings for your monitor resolution of course

Now run winecfg (while steam is open) and set the windows version to Windows 98

Now start the game and enjoy. It should work perfectly.

When you exit steam, run winecfg again and set it to Windows 2000. The games need Win98 mode to avoid crashing due to a font problem and Steam needs to be started in Windows 2000 mode.

ENJOY! [/QUOTE]

[http://forums.facepunchstudios.com/showthread.php?t=539582](http://forums.facepunchstudios.com/showthread.php?t=539582)

---

### Post by OpposingForce on 2008-05-20
Update CS 1.6 seems to be working now.  I can hear sound in game and can connect and play on multiplayer servers.  However hl1 still has no sound.

---

### Post by OpposingForce on 2008-05-21
Bump just installed Half Life: Blue Shift and I get the same bug.  Sound in the main menu, but no sound in game.  Again, CS 1.6 works and it runs on the same engine as these games.  The settings in the "options" box are the same also in all 3 games.

---

### Post by OpposingForce on 2008-05-22
So I guess no one can help

---

### Post by OpposingForce on 2008-05-22
Update : Just tried to join a multiplayer server in half life 1.6  Sound works in game when I'm on a multiplayer server.  This must be why it worked in Counter Strike 1.6.  The sound in 1.6 didnt work until I joined a multiplayer game.  However, in half life sound doesn't work in single player.  Anyone have any ideas?

---

### Post by OpposingForce on 2008-05-25
bump

---

### Post by OpposingForce on 2008-05-26
bump

---

### Post by OpposingForce on 2008-05-27
UPDATE: HL1 single player now has sound.  All I had to do was click "Driver Emulation" in the Wine Cfg. - Audio tab and sound worked.

I apologize for the multiple bumps, but I was losing my patience with this issue over the last couple days.  Funny how it was solved by a single click.  Lol.

---

### Post by xblackxphoenix on 2008-08-12
i had sound problems with half-life steam and non-steam

half-life non-steam really just sucked bad in terms of video, but that mightve been due to the fact that i didnt install it from the cd, i took the game files off my external and launched from there. the video sucked so bad that i didnt even bother messing with the sound.

for half-life steam, it worked perfectly but still no sound and thats when i found this thread. and at the same time i remembered i was having sound problems with another game awhile back, and i had to enter "killall pulseaudio" to get the game's sound to work. i tried that for half-life steam and then the sound worked agian!

---

### Post by QwUo173Hy on 2008-09-23
What version of ubuntu are you guys using? I'm on Hardy with wine 1.0. I have HL1 without steam and I can't get sound.
Tried checking driver emulation and killing pulseaudio as suggested but no difference.

OpposingForce, what drivers (if any) do you have checked under the Audio tab in winecfg?

---

### Post by QwUo173Hy on 2008-09-23
Sorry, I just checked the Alsa box and it works now. I had unchecked everything but checked driver emulation. Checking both driver emulation and Alsa driver got it working. I also have pulseaudio killed at the moment. Not sure if that's necessary though.

---

