---
title: "[SOLVED] Will I be able to run WoW? Dell inpiron 9300"
date: 2008-11-23
forum: Wine
---

### Post by methodmarvel on 2008-11-23
I have a two-three year old dell inspiron 9300 laptop

It has an intel pentium m 1.73ghz, an ATi300mobility graphics card128MB (I think..) and 757MB RAM

I can install and get 3d effect running ok with both the ubuntu repo restricted driver and better with envyNG but I've never really got anywhere with WINE

I tried to install morrowind a little while ago which resulted in no video but I only tried for a few hours or so to get it to work

I ran "glxinfo | grep rendering" and was given the all clear "direct rendering: Yes"

I've been looking at this [https://help.ubuntu.com/community/WorldofWarcraft#Configuration](https://help.ubuntu.com/community/WorldofWarcraft#Configuration) and can't see what I have been doing wrong

I've never had much luck with WINE. Any ideas?

---

### Post by methodmarvel on 2008-11-25
So it is possible but with a lot of compromise (run in window only, run only super low graphics/sound etc).

If anything below isn't clear I apologize - I do not remember if this is everything as I sort of worked rather blindly. I also don't remember if this is the exact order I did it - but I think it's close. For the most part I used the guide at [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) but also made some changes I learned about failing to get morrowind to run.

I installed envyNG and let it auto setup my ATi graphics card and install the driver. envyNG is in the repos and on ubuntu you want to go to the synaptic package manager and install the "envyng-gtk" package.

I installed the latest version of wine from the wine repo (1.1.9). You can find out how to do this at [https://help.ubuntu.com/community/WorldofWarcraft#Installing%20Wine](https://help.ubuntu.com/community/WorldofWarcraft#Installing%20Wine)

I was installing the 10-day trial of WoW and it a few snags - the WoW downloader client works but you have to move the windows around a look for an error box hidden under your other windows - you must click ok on this before your download will start. From there I just followed the instructions as per a normal windows system.

To setup wine I followed [https://help.ubuntu.com/community/WorldofWarcraft#Configuration](https://help.ubuntu.com/community/WorldofWarcraft#Configuration) :

In **wtf** I did add
SET ffxDeath "0"
SET ffxGlow "0"
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"
SET gxApi "opengl"

My whole wtf looked like this
SET locale "enGB"
SET videoOptionsVersion "1"
SET movie "0"
SET realmList "eu.logon.worldofwarcraft.com"
SET patchlist "eu.version.worldofwarcraft.com"
SET coresDetected "1"
SET hwDetect "0"
SET gxResolution "800x600"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET Gamma "1.000000"
SET readTOS "1"
SET readEULA "1"
SET readTerminationWithoutNotice "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "177"
SET particleDensity "1.000000"
SET spellEffectLevel "0"
SET textureFilteringMode "0"
SET baseMip "1"
SET environmentDetail "0.5"
SET weatherDensity "0"
SET ffxGlow "0"
SET ffxDeath "0"
SET Sound_OutputQuality "0"
SET mouseSpeed "0.5"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET realmName "Terokkar"
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"
SET gameTip "19"
SET uiScale "0.91999995708466"
SET gxVSync "0"
SET gxApi "opengl"
SET gxColorBits "24"
SET gxDepthBits "24"
SET checkAddonVersion "0"
SET lastCharacterIndex "1"
SET Sound_EnableErrorSpeech "0"
SET Sound_EnableMusic "0"
SET Sound_EnableEmoteSounds "0"

**winecfg** was set to generally default (windows xp)
on the graphics tab I selected emulate virtual desktop 800x600 (note, it doesn't work in full screen and lower resolution resulted in a better frame rate - 40fps sometimes upto 50fps)
I set audio to ALSA, basic, 44100, 16bits

**regedit** was a bit complex - not sure how much of this is needed
HKEY_CURRENT_USER software wine
add new key name it "Direct3D" without the ""
in "Direct3D" right click and create new string values
"OffscreenRenderingMode" with the value "fbo"
"UseGLSL" with the value "Enabled"
"VideoMemorySize" with the value "32" (note, specific to my graphic card, make sure you have the same setup following this guide)

also in HKEY_CURRENT_USER software wine
add another new key "OpenGL"
create a new string value
"DisabledExtension" with the value "GL_ARB_vertex_buffer_object"

I hope that generally helps. My launcher runs ```
wine "/home/username/.wine/drive_c/wowtrialfolder/World of Warcraft Trial/Launcher.exe"
```

As far as I'm aware it's running directx not opengl at all - It was slower when I added the -opengl to the launcher command so I assume that the regedit key opengl is unnecessary but I'll leave it in as it isn't causing any harm I'm aware of.

As for the run it's ok - I've turned the graphics setting low and a lot of the sounds off. The walking animation seems to have a minor regular gitter but you can ignore it.

Any questions post here and I'll try to untangle my memories of getting it to work.

[IMG]http://lh4.ggpht.com/_N0d9xGSt9-M/SSwGd_VASQI/AAAAAAAAAF4/VsNLqxyfUR8/s800/Screenshot-5.png[/IMG]

[IMG]http://lh6.ggpht.com/_N0d9xGSt9-M/SSwGeIPNgbI/AAAAAAAAAGA/51XtrFv0WkY/s800/Screenshot-7.png[/IMG]

---

### Post by binbash on 2008-11-25
with that card and current ati drivers, if i were you, i should not bother to try WoW

---

### Post by Eviljim on 2008-11-25
> In wtf I did add
SET ffxDeath "0"
SET ffxGlow "0"
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"
SET gxApi "opengl"

If you added the last line in this list to your config.wtf file then you **are** running in opengl mode. The ATI cards dont run at all under direct3d, since the ubuntu ATI drivers only really support OpenGL. 

You can check this by substituting the "OpenGL" part for "Direct3d" and then running the game.

However since WoTLK, the minimum required graphics card has now increased due to the new shader/special effects that are being used.

---

### Post by methodmarvel on 2008-11-30
> **binbash said:**
> with that card and current ati drivers, if i were you, i should not bother to try WoW

It was in part experiment - I know my computer is behind the times and without windows drivers would have a hard time - but I was successful as I got it working.

As for not bothering to play WoW there's plenty of other reasons not to play including preservation of physical fitness.

---

### Post by methodmarvel on 2008-11-30
> **Eviljim said:**
> If you added the last line in this list to your config.wtf file then you **are** running in opengl mode. The ATI cards dont run at all under direct3d, since the ubuntu ATI drivers only really support OpenGL. 

You can check this by substituting the "OpenGL" part for "Direct3d" and then running the game.

However since WoTLK, the minimum required graphics card has now increased due to the new shader/special effects that are being used.

ah - so the .wtf dictates what mode it's in not wine/a command?

---

