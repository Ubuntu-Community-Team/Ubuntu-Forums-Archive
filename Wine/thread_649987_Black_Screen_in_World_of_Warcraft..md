---
title: "Black Screen in World of Warcraft."
date: 2007-12-25
forum: Wine
---

### Post by Tsuzanxi on 2007-12-25
[B]Help! I'm only getting a black screen (with a strange silhouette of the login) when I start up the game.  I'm running with an Athlon XP 2800 with an Nvidia Geforce4 MX Integrated GPU.  I should also have the latest drivers since I recently installed them via Envy.
I understand the specs arn't too impressive but the game displayed properly when I first launched it, upon logging into my account and updating the game I've had no luck.
[EDIT] I forgot to add, sound runs fine. If I get the opening movie to play too that sounds fine as well. And I've added a screenshot.
I've recorded my terminal log once the game starts - [/B]

[I]fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c0f0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c0f0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33ed84,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ecac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f40c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f588,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f580,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f55c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33f124,0x00000000), stub!

fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:imm:ImmAssociateContextEx (0x20024, (nil), 16): stub
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)[/I]

[B]I've only had Linux for a little while so this is all foreign to me. 
Here's a sample of my config.wtf as well -[/B]

[I]SET gxResolution "800x600"
SET gxRefresh "60"
SET hwDetect "0"
SET movie "0"
SET readTOS "1"
SET gxMultisampleQuality "0.000000"
SET readEULA "1"
SET readScanning "-1"
SET gameTip "54"
SET gxCursor "0"
SET SmallCull "0.040000"
SET frillDensity "32"
SET farclip "357"
SET Gamma "0.600000"
SET MusicVolume "0.60000002384186"
SET SoundVolume "1"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET MasterVolume "1"
SET ffx "0"
SET AmbienceVolume "0.60000002384186"
SET uiScale "1"
SET mouseSpeed "1"
SET cameraPitchMoveSpeed "90"
SET cameraYawMoveSpeed "180"
SET cameraPitchSmoothSpeed "45"
SET cameraYawSmoothSpeed "180"
SET cameraSmoothStyle "0"
SET cameraSmoothTrackingStyle "0"
SET cameraDistanceMaxFactor "1"
SET SoundZoneMusicNoDelay "1"
SET gxColorBits "24"
SET statusBarText "1"
SET ffxDeath "0"
SET minimapZoom "0"
SET guildMemberNotify "1"
SET profanityFilter "0"
SET readContest "-1"
SET minimapInsideZoom "5"
SET gxDepthBits "24"
SET locale "enGB"
SET coresDetected "1"
SET videoOptionsVersion "1"
SET expansionMovie "0"
SET showToolsUI "1"
SET Sound_OutputDriverName "Realtek ALC650F"
SET realmList "eu.logon.worldofwarcraft.com"
SET patchlist "eu.version.worldofwarcraft.com"
SET M2UseShaders "0"
SET gxWindow "1"[/I]

**I believe that my config.wtf could quite possibly do with some tidying up also.  If anyone can help, you're much welcome to have a cookie.**

---

### Post by Tsuzanxi on 2007-12-29
... sigh. No help?

---

### Post by TolTime on 2007-12-29
im having the same problem, and I'm also new to linux, been trying to get WOW to work with WINE for awhile.
the only thing i could think to add is this 

SET gxApi "OpenGL"

to the WTF File, that might help

---

### Post by Kodge on 2007-12-30
It's your graphics card. Many players running windows, and Mac osx are getting this problem.
I believe the solution was to update your graphic card drivers, or reinstall them. I can't quite remember. However check on there tech support forums ( EU or US ). You're sure to find your answer.

---

