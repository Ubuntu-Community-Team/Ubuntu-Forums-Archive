---
title: "[SOLVED] WOW causes X to crash"
date: 2008-01-18
forum: Wine
---

### Post by aliencam on 2008-01-18
Many WOW issues in WINE.. 

[B]
Summary: [/B]

WOW worked terribly, at like 2-8 FPS. I tried upgrading WINE and now WOW crashes X.  When WOW was running at 2 FPS it was barely using any of the CPU power and little memory. Most of the time the CPU was not even throttled all the way up to 1.8 GHz, but it was at 800MHz or 1.2GHz usually.

**My Computer's Specs**
Lenovo x61 Tablet
Ubuntu Gutsy 7.10
Video Card: Intel Graphics Media Accelerator X3100
Intel Core 2 Duo 1.8 (L 7700) 
3 GB DDR2 PC5200


[B]
What I have done (or, what might have caused the problem), or "a history of WOW on my computer":  [/B]

installed wine from ```
sudo apt-get install wine
``` (but I did not add the winehq repository, i just added it from whatever is in the normal (enabled everything) ubuntu repos. ) (or i might have installed from add/remove programs/synaptic)

started off installing WOW with WINE and no extra config. it ran at 2 FPS. 

i did the registry hack for opengl

added the following to config.wtf: 
```

SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"

```

wow opened, but there were no models at all, the only thing I could see was the environment (no characters/plants/ anything else) wow ran at 2 FPS still
[I]
Installed Cedega, installed WOW in Cedega, same framerate. Uninstall WOW in Cedega, uninstall Cedega, back to WINE. [/I]

I removed 
```
SET gxApi "opengl"
```
from config.wtf

WOW ran at 2 FPS again, just like it did the first time. still unplayable. 

googled for awhile, found [http://www.wowwiki.com/Linux/Wine/Troubleshooting](http://www.wowwiki.com/Linux/Wine/Troubleshooting)

added back to config.wtf
```
SET gxApi "opengl"
SET M2UseShaders "0"
```

WOW ran semi-usably, at 8 FPS (usable for 15 minutes until I go crazy)

so I tried running the script to run WOW on it's own xsrv, it did not work. all I ever got was an empty X window, and I switched back to X-0 with ctrl-alt-f7

realized I had an "old" version of WINE (whatever was in the repos) so I did 
```
 sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/winehq.list
``` then did  ```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
 sudo apt-get update
 sudo apt-get install wine
```
and I ran winecfg again (it was the same as it was before) 

the next time I started WOW, I get the loader, and when I click "Play" , the screen goes black and x starts over. (the exact same way as if one were to press ctrl-alt-backspace) 

I've tried restarting the computer and doing it again, WOW always crashes/restarts X.  I don't know where the X log is or whatever it is i need to look at.  I tried running WOW from the terminal, but I can't see the output because X restarts. 


**notes: **
ASLA sound works fine.  I can hear sound.  I would rather not switch WINE to OSS, or add the 
```
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
```
lines to config.wtf.  (because those only control sound as far as I know, and my sound works fine) 

[B]
Config.WTF file: [/B]

```
SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET SmallCull "0.080000"
SET DistCull "350.000000"
SET frillDensity "8"
SET farclip "400.000000"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET realmList "us.logon.worldofwarcraft.com"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET coresDetected "2"
SET videoOptionsVersion "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET patchlist "us.version.worldofwarcraft.com"
SET realmName "Draenor"
SET gameTip "6"
SET ffxDeath "0"
SET ffxGlow "0"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET mouseSpeed "1"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "1"
SET UberTooltips "0"
SET M2UseShaders "0"
SET gxApi "opengl"
SET textureFilteringMode "0"
```


**Terminal Log from when WOW was working at low FPS:**
```
cameron@camubuntux61tab:~$ '/home/cameron/.wine/drive_c/Program Files/World of Warcraft/Wow.exe' 
ALSA lib ../../src/conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed84,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34ecac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f2a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f40c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f588,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f580,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f124,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f508,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f4f8,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x34efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f124,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:reg:GetNativeSystemInfo (0x374029c4) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x7d49c4a4) stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:win:EnumDisplayDevicesW ((null),0,0x34d1a4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34d200,0x00000000), stub!
fixme:imm:ImmAssociateContextEx (0x30024, (nil), 16): stub
cameron@camubuntux61tab:~$ 
```

---

### Post by orionsbelt on 2008-01-19
I am having a similar error message (and process), with different results.  I'm running Feisty with an nVidia 7600 GT card, as I couldn't get my video card to work with Gutsy.

Instead of a bad framerate, I'm having graphical glitches:  Other characters (and my own) do not appear unless they are shape-shifted.

Did you have any luck resolving this issue?  

Will cross-post in hopes of getting a response.

---

### Post by orionsbelt on 2008-01-19
Of course after I posted, I managed to find my own answer.

I followed the instructions on [http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine#Graphical_glitches]("http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine#Graphical_glitches") for dealing with graphical glitches.  in other words, i did this:

"Do the registry tweak as described her: [HOWTO_Install_and_update_World_Of_Warcraft_with_wine#OpenGL_Registry_Edit]("GL_ARB_vertex_buffer_object") but enter Gl_ARB_vertex_buffer_object;GL_ARB_vertex_program in the last step.

Add the following to your Config.wtf:

SET M2UsePixelShaders "1"
SET M2UseShaders "0
SET UIFaster "2"

however, when that happened wow did not start.  i decided to switch back to the way it was, removed the extra script from Config.wtf, and set the "Disabled Extensions" in regedit back to "GL_ARB_vertex_buffer_object".

i logged on, and it suddenly worked.  i am not sure if i incorrectly enterred "GL_ARB_vertex_buffer_object", or my computer decided it liked me again.

hope this helps.

---

### Post by aliencam on 2008-01-19
nope I tried both of those, they didn't do anything. 

I was able to fix X from crashing, by removing the WINEHQ key from my sources list, and sudo apt-get remove wine, then sudo apt-get install wine.  it now runs, only at 2-8 FPS.

---

