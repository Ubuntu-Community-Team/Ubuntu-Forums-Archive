---
title: "Many world of warcraft problems"
date: 2008-11-13
forum: Wine
---

### Post by pankirk on 2008-11-13
Ok, so I installed wine (version 1.1.8!) and I figured that world of warcraft would install flawlessly and that I would be playing as soon as the game isntalled! So, I downloaded the game (and the burning crusade patch) and both installs went great. So, I then proceded to install the frist patch that I have which is labled "" and right when its "done" updating, I get this:
> Bluzzard updater was unable to read the file "C:\Program files\world of warcraft\data\enUS\expansion-locale-enUS.MPQ". This error may be caused by problems with the media or deive at C:\--for example, a scratched or dirty.......... blah blah you get the error message. And then the error goes on down to say:(The data being read was "Interface\GLUES\MODELS\UI_MainMenu_BurningCrusade\UI_MainMenu_BurningCrusade.m2" and the error code was 4).

So, I go to look at the console screen and it's got a bunch of useless crap in it like:

> 
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x136274)->((null) 1 0x33e5d0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x136274)->((null) 25 2 0x33e5e4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x136274)->((null) 26 2 0x33e5e4 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x136274)->(0x33e620)
fixme:shdocvw:ClOleCommandTarget_Exec (0x136274)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33e6f4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x136274)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x33e784)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c 81 0 33d79c)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c 83 0 33d74c)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c 1 0 33d79c)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c 5 0 640064)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c 3 0 0)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10044 210 1 1004c)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004e 81 0 33d89c)




AND so now i'm wondering, can this be related to the problem I get when I'm trying to actually start the game (I mentioned that the game crashes on start up right? oh.)? That error message is as follows:

> 
-

This application has encountered a critical error:

ERROR #131 (0x85100083) File Corrupt
Program:	C:\Program Files\World of Warcraft\WoW.exe
File:	Data\enUS\expansion-locale-enUS.MPQ




WoWBuild: 6080


So at this point I'm extremely lost. It looks like WoW is having trouble reading my files? I don't know. I would like to point out that I'm pretty competent at using the computer and In general I know what I'm doing. But this, I'm completely lost! I want to thank you for reading this all and I hope you can please find the time to help me! :guitar:



EDIT::::: SHould I add my Config.wtf? Well, here it is:
> 
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enUS"
SET hwDetect "0"
SET gxResolution "800x600"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET SmallCull "0.010000"
SET DistCull "350.000000"
SET frillDensity "8"
SET farclip "417"
SET particleDensity "1.000000"
SET movie "0"
SET expansionMovie "0"
SET readTerminationWithoutNotice "-1"
SET coresDetected "2"
SET videoOptionsVersion "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET patchlist "us.version.worldofwarcraft.com"
SET spellEffectLevel "0"
SET gameTip "7"
SET gxWindow "1"
SET gxMaximize "1"
SET gxTripleBuffer "1"
SET gxVSync "0"
SET windowResizeLock "1"
SET textureFilteringMode "0"
SET DesktopGamma "1"
SET Gamma "1.000000"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET baseMip "1"
SET groundEffectDist "70"
SET weatherDensity "0"
SET ffxGlow "0"
SET ffxDeath "0"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET uiScale "1"
SET shadowLOD "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "OpenGL"


---

