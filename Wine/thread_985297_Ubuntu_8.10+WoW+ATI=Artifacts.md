---
title: "Ubuntu 8.10+WoW+ATI=Artifacts"
date: 2008-11-17
forum: Wine
---

### Post by pawnshark on 2008-11-17
I have recently done a fresh install of Ubuntu 8.10 Intrepid and installed WoW using this guide 

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) 

I can get the game to run but momentarily after login, glitches that I can only assume to be artifacts appear.  Attached is my config.wtf and a screenshot of the problem

```

SET locale "enUS"
SET portal "us"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET movie "0"
SET expansionMovie "0"
SET mouseSpeed "0.5"
SET Gamma "1.000000"
SET readTOS "1"
SET readEULA "1"
SET showToolsUI "1"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET Sound_OutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "177"
SET particleDensity "1.000000"
SET realmName "Durotan"
SET gameTip "12"
SET VoiceActivationSensitivity "0.39999997615814"
SET gxApi "opengl"
SET ffxGlow "0"
SET M2UseShaders "0"
SET gxWindow "1"
SET lastCharacterIndex "2"
SET gxVSync "0"
SET textureFilteringMode "0"
SET baseMip "1"
SET spellEffectLevel "0"
SET environmentDetail "0.5"
SET weatherDensity "0"
SET ffxDeath "0"
SET uiScale "1"
SET useUiScale "1"

```

[IMG]http://lh3.ggpht.com/_pNI3RYjx7GY/SSHJJuU73rI/AAAAAAAAACA/q3K7wwnMpts/s800/Screenshot-World%20of%20Warcraft.png[/IMG]

---

### Post by Progressive on 2008-11-17
This is very similar to my problem in Oblivion:

[http://ubuntuforums.org/showthread.php?t=984826](http://ubuntuforums.org/showthread.php?t=984826)

I am certain it is the ATI drivers and I have tried everything to fix it to no avail.

Deus Ex is still working, so I can only assume it is a problem with the shaders. You can try looking for shader fixes or turning off shaders. That is your best bet until this problem is fixed.

Do you have the 8.10 Catalyst Driver? I haven't tried upgrading, since the features didn't seem that impressive. Yet, you could try that. If not then you'll force me to try that, and I am lazy.

---

### Post by pawnshark on 2008-11-17
I did a fgl_glxgears -info in terminal and got this 

```
pawnshark@ubuntu-x64:~$ fgl_glxgears -info
Using GLX_SGIX_pbuffer
GL_RENDERER   = RADEON X850 XT
GL_VERSION    = 2.1.8087 Release
GL_VENDOR     = ATI Technologies Inc.

```

I know its not the best way to get driver data but it looks like I have version 8.08?  I got the drivers via the Ubuntu Hardware Drivers option under System -> Administration -> Hardware Drivers

So far I have turned the settings to minimum on WoW and the SET M2UseShaders "0" should turn off all shaders.  Newer drivers may be the fix, but I'm lazy also, given that installing ATI linux drivers are quite painful from past experience.

---

### Post by Progressive on 2008-11-17
If you go to your utilities menu and select Catalyst Control Center, the Information tab should say driver version 8.54.3 if you have Intrepid.

Turning off shaders should do it, but you will get crappy graphics. There were shader fixes for Oblivion that didn't fix my problem, but perhaps there are some for WoW that do work. You never know.

Of course, just turning off shaders is easier and more likely to solve the problem.

---

### Post by pawnshark on 2008-11-17
Ah yes, I have driver version 8.54.3 according to ATI's Catalyst Control Center.  

They have a new 8.11 Driver on the ati.amd.com site, but I'm a little wary on the outcome of that.  Think I might have to wait till its released on the restricted drivers list.

---

### Post by pawnshark on 2008-11-25
Woohoo!

Well after much forum searching, a "solution" was found.  It is actually from another thread on this forum that described itself as a performance enhancement and not as a fix.  But hey, whatever works.\\:D/

According to [http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378) the "Almost mandatory performance enhancing tweak" was used to fix the problem.  It reads

> 
Almost mandatory performance enhancing tweak
This is a simple registry edit for Wine that will dramatically increase the framerate in game for both ATi and nVidia users.

Open a terminal window, type regedit and press enter. This will start the Wine equivalent of the windows registry editor. If you are familiar with using the registry editor under windows then this is pretty much the same.

Notice: the guide below is case sensitive!

1. Find this key HKEY_CURRENT_USER\Software\Wine\
2. Highlight the wine folder in the left hand pane by clicking left on it. The icon should change to an open folder
3. Right-click on the wine folder and select [NEW][KEY]
4. Replace the text New Key #1 with OpenGL
5. Right-click in the right hand pane and select [NEW] then [String Value]
6. Replace New Value #1 with DisabledExtensions
7. Then double click anywhere on the line, a dialog box will open.
8. In the value field type GL_ARB_vertex_buffer_object


So, give that a shot and hope for the best.  Also, I'm a forum noob so if I didn't credit the source correctly or need to change something let me know.

---

### Post by Progressive on 2008-11-25
That fix does seem very likely to be a universal fix if it worked for you. This is very very exciting!

Thank you for notifying me of this. I wish I were back in my dorm to test this out, but it will have to wait until after thanksgiving.

I will post this on WineHQ to see if this fixes it for them. Thanks again.

Cheers!

P.S. You cited it correctly. Simply linking is fine.

---

### Post by multiboot on 2009-05-15
This worked for me. Thanks for posting!

:KS:KS:KS:KS:KS

P.S. For posterity, I'm running Hardy on an Athlon 2600+, 1.5 GB RAM and an AGP Radeon x1600 (the reason I run Hardy because of driver support)

---

