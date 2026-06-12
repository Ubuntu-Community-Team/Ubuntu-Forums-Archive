---
title: "World of warcraft fps and mouse issue in hardy heron"
date: 2008-06-26
forum: Wine
---

### Post by Kharny on 2008-06-26
Hi, I'm currently trying to run world of warcraft in a clean install of hardy heron(8.04) with then newest version of wine.

I've done the install, updated my nvidia drivers to the newest ones on nvidia.com and done the registry tweak and the config tweak.

Unfortunately, not only is the fps 1 or even worse, the mouse moves very slowly and everything is horribly sluggish.

wondering if I am doing something wrong or if it's either HH or the new 2.4.x patch

---

### Post by thisismalhotra on 2008-06-26
> **Kharny said:**
> Hi, I'm currently trying to run world of warcraft in a clean install of hardy heron(8.04) with then newest version of wine.

I've done the install, updated my nvidia drivers to the newest ones on nvidia.com and done the registry tweak and the config tweak.

Unfortunately, not only is the fps 1 or even worse, the mouse moves very slowly and everything is horribly sluggish.

wondering if I am doing something wrong or if it's either HH or the new 2.4.x patch

Are you using OpenGL or D3D. Nvidia has very good supprt for both.

Try to follow thse guides but as short fix try launching WoW with -opengl switch.

or add to you config.wtf as show on the guide.

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

GL
FTW

---

### Post by Kharny on 2008-06-26
Using opengl, and did the config.wtf edits and regedit, used that exact same guide for installing :D

And while I know glxgears isn't a benchmark, is it really weird to get sub-500 fps there?

ps. the machine is a acer aspire 5520 with amd64, nvidia 7000M, I know it's not the best, but it should be playable atleast.

---

### Post by flytripper on 2008-06-26
maybe its a 64 bit issue..

---

### Post by Kharny on 2008-06-26
Well, that might just be it. After researching a while, it seems that the wine installation doesn't put the 32 bit files any more.

Missing atleast /usr/local/lib/wine/opengl32.dll

anyone know if this might be the problem and how to solve it?


edit: weird sentance build

---

### Post by Kharny on 2008-06-27
Installed ubuntu 8.04 32 bit. no changes.

# Wine version - 1.0 new today, clean installed
# Terminal output - 

```
fixme:advapi:SetSecurityInfo stub
archive Data\patch.MPQ opened
archive Data\enGB\patch-enGB.MPQ opened
archive Data\enGB\patch-enGB-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\common.MPQ opened
archive Data\enGB\locale-enGB.MPQ opened
archive Data\enGB\speech-enGB.MPQ opened
archive Data\enGB\expansion-locale-enGB.MPQ opened
archive Data\enGB\expansion-speech-enGB.MPQ opened
fixme:powrprof:DllMain (0x7ca20000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7ca20000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x32eda4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ec94,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f2c8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f42c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f528,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f518,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f144,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:reg:GetNativeSystemInfo (0x37402bc4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmReleaseContext (0x20024, 0x1326b8): stub
Unable to read extra attributes: "Cache\Survey.mpq"
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:win:EnumDisplayDevicesW ((null),0,0x32d194,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32d200,0x00000000), stub!
fixme:imm:ImmAssociateContextEx (0x20024, (nil), 16): stub

```

# Hardware specs/drivers -newest nvidia drivers

Some testing i did, mouse works fine in d3d mode, but fps is around 5 in non-busy area.s.
In opengl mode, fps is around 10, but input is sluggish.
Desktop effects are turned off

---

### Post by IamReck on 2008-06-27
Could you please post your "config.wtf" file?

---

### Post by Kharny on 2008-06-27
```
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "1"
SET locale "enGB"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "51"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET pixelShaders "1"
SET movie "0"
SET expansionMovie "0"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET realmList "eu.logon.worldofwarcraft.com"
SET patchlist "eu.version.worldofwarcraft.com"
SET SmallCull "0.070000"
SET DistCull "500.000000"
SET farclip "177"
SET particleDensity "1.000000"
SET spellEffectLevel "0"
SET groundEffectDensity "24"
SET textureFilteringMode "0"
SET Gamma "1.000000"
SET lastCharacterIndex "4"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET lod "1"
SET baseMip "1"
SET groundEffectDist "70"
SET weatherDensity "0"
SET ffxGlow "0"
SET ffxDeath "0"
SET realmName "Dragonblight"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET gameTip "5"
SET uiScale "1"
SET shadowLOD "0"
SET gxApi "opengl"
```

Is there any way to see/test if the game/wine is running hardware or software rendering?

---

### Post by IamReck on 2008-06-27
[FONT=monospace]What kind of NVIDIA card do you have?

Also, go into terminal, and type this [/FONT]
```

glxinfo | grep rendering


```
Paste the output here.

I would also try setting WoW on Minimal Video and Sound settings.  Do you have a firewall installed?

---

### Post by flytripper on 2008-06-27
it may just be the vidieo card mine is a nvidia7600gt p4 2.8 x86 and it only runs 40fps out of cities and underbog and kara ^

as far as i am aware, running it in wine gives it a whole extra layer to go through which means you need extra proccessing power..
dont quote me though please i'm only starting out in ubuntu myself.

---

### Post by Kharny on 2008-06-29
ok, info from the glx info:

```
direct rendering: Yes
```

flytripper, i'd settle for 40 fps, currently getting around 5-10 fps in the barrens

---

### Post by IamReck on 2008-06-29
What are the specifications on your machine?  Do you have Windows on it?

---

### Post by thisismalhotra on 2008-06-30
One more thing do you have compiz ON(Dekstop Special effects), turning it off before you start to play is always a good idea.

This may not work, but I have had issues with nvidia installer in past. What I always do and you may try the same is uninstall you nvidia driver and install envy-ng and envy-gtk and install drivers through there. Than run winecfg again and set it up to use windows xp settings. See if that works for you.

Here is a link for ENVY

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

EDIT: WINE 1.1.0 has been released upgrade and see if that helps somehow.

---

