---
title: "World of Warcraft"
date: 2007-12-26
forum: Wine
---

### Post by TolTime on 2007-12-26
i have looked through many posts about using WINE to run world of warcraft.  I can't seem to find anyone with my same problem i installed World of warcraft and ran the Launcher.exe 

i then get to the screen that gives me the option to play, once i click on play i get an error that states

Failed to open archive Data/common.MPQ

i don't have any idea how to resolve this problem

---

### Post by hikaricore on 2007-12-26
Sounds like your mpq files are corrupted.
I'd suggest reinstalling or attemping to use the blizzard repair utility.

Other than that, don't use Launcher.exe it will just hinder your progress.

Launch WoW properly /w WoW.exe.

---

### Post by TolTime on 2007-12-26
ok, the fresh install worked, but now once the game boots up, the network strengh icon flashes during the intro video. And once the videos end the game shuts down

---

### Post by hikaricore on 2007-12-27
Disable the video playback in your Config.wtf file.

Aside from that you may want to mention to us your video hardware and how you installed the drivers for said hardware.
Also are you running the game in OpenGL or DX mode?  OpenGL is recommended, however some low quality video hardware has little support for OpenGL and DX is your only alternative.

---

### Post by TolTime on 2007-12-27
I'm using a Intel Graphics Media Accelerator 900, 

i found a post saying
"Intel's graphics drivers are open source, they are shipped by default in Ubuntu. You don't have to install anything." is that correct?

 
Also i am running it in OpenGl

looking through the files, i can not fine config.wtf file

---

### Post by TolTime on 2007-12-27
bump

---

### Post by hikaricore on 2007-12-27
Please refrain from bumping your post for 24-48 hours.  It is often considered rude and just plain unneeded to do so.

---

### Post by TolTime on 2007-12-31
This is my WTF file

SET locale "enUS"
SET hwDetect "1"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET doodadAnim "0"
SET SmallCull "0.080000"
SET DistCull "350.000000"
SET frillDensity "8"
SET farclip "350.000000"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "0.900000"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET realmList "us.logon.worldofwarcraft.com"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "opengl"

i am running it in opengl mode
i don't know how to turn off the video play back
screen is black and the music sounds like it is lagging, cutting in and out

---

### Post by TolTime on 2007-12-31
*UPDATE*

SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET doodadAnim "0"
SET SmallCull "0.080000"
SET DistCull "350.000000"
SET frillDensity "8"
SET farclip "350.000000"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "0.900000"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET realmList "us.logon.worldofwarcraft.com"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "opengl"
SET coresDetected "1"
SET videoOptionsVersion "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "dmix:0"
SET patchlist "us.version.worldofwarcraft.com"
SET ffxDeath "0"
SET ffxGlow "0"
SET Sound_VoiceChatInputDriverName "dsnoop:0"
SET Sound_VoiceChatOutputDriverName "dmix:0"
SET realmName "Shadowsong"
SET gameTip "2"

I have now been able to login to the game
i added

SET ffxDeath "0"
SET ffxGlow "0"

to the WTF. file
the pictured attached is showing what problem i am having with the graphics now.  
Has anyone had this problem?

---

### Post by TolTime on 2008-01-01
I ran wow through terminal and got this output

terence@ternce-laptop:~$ env WINEPREFIX="/home/ternce/.wine" wine "C:\Program Files\World of Warcraft\Launcher.exe"
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
terence@ternce-laptop:~$ fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed78,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34eccc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f29c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f400,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f57c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f574,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f4fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f4ec,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x34efd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f118,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:reg:GetNativeSystemInfo (0x374029c4) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x781de494) stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x34c488,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x34c488,0x00000000), stub!
totolfixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:win:EnumDisplayDevicesW ((null),0,0x34d198,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34d1f4,0x00000000), stub!
fixme:imm:ImmAssociateContextEx (0x30024, (nil), 16): stub


i don't know if this can help.
The WTF, is in the previous post,
The only problem with the game is the visual aspect.
Can any more changes be made to the WTF for the game to be playable

---

### Post by TolTime on 2008-01-06
bump

---

