---
title: "Football Manager 2012 on Ubuntu"
date: 2011-11-17
forum: Wine
---

### Post by AnoopSivarajan on 2011-11-17
Successfully installed FM 2012 on Ubuntu 11.10. Checkout the following link for more details.

[http://asivarajan.blogspot.com/2011/11/football-manager-2012-on-ubuntu-1110.html](http://asivarajan.blogspot.com/2011/11/football-manager-2012-on-ubuntu-1110.html)

---

### Post by sionco on 2011-11-28
Thanks, this is fantastic!

but just a note, that you have to launch the game from within playonlinux, not from the folder.

---

### Post by ergo-proxy on 2011-11-29
> **AnoopSivarajan said:**
> Successfully installed FM 2012 on Ubuntu 11.10. Checkout the following link for more details.

[http://asivarajan.blogspot.com/2011/11/football-manager-2012-on-ubuntu-1110.html](http://asivarajan.blogspot.com/2011/11/football-manager-2012-on-ubuntu-1110.html)

Please mark your thread as solved and submit your test results on winehq :)

---

### Post by wild_oscar on 2011-12-02
Would be awesome if it worked. However, for me, after running the intro and going to "loading/cargando..." screen, it closes unexpectedly. Wine output is:

> fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:gameux:GameExplorerImpl_VerifyAccess (0x14c030, L"M:/.PlayOnLinux/wineprefix/fm2012/drive_c/Program Files/SEGA/Football Manager 2012/fm.exe", 0x32fad8)
fixme:userenv:RegisterGPNotification 0xb4 0
fixme:userenv:RegisterGPNotification 0xb8 1
fixme:module:load_library unsupported flag(s) used (flags: 0x00000060)
fixme:nls:GetGeoInfoW -1 4 0x32eec0 3 0
fixme:nls:GetGeoInfoW -1 4 0x32f338 3 0
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x10074 0x00000000
fixme:win:EnumDisplayDevicesW ((null),0,0x52ae3b8,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x2007a 0x00000000
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d:wined3d_device_reset Cannot change the back buffer count yet.
fixme:d3d:wined3d_device_reset Cannot change the back buffer count yet.
fixme:d3d9:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0xffffffff
fixme:d3d:wined3d_device_reset Cannot change the back buffer count yet.
fixme:d3d9:wined3dformat_from_d3dformat Unhandled D3DFORMAT 0xffffffff
fixme:win:EnumDisplayDevicesW ((null),0,0x52adf24,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x52adf24,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f3a4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f3a4,0x00000000), stub!
fixme:wtsapi:WTSUnRegisterSessionNotification Stub 0x2007a
fixme:wtsapi:WTSUnRegisterSessionNotification Stub 0x10074


---

### Post by claudiumsh on 2011-12-28
> **wild_oscar said:**
> Would be awesome if it worked. However, for me, after running the intro and going to "loading/cargando..." screen, it closes unexpectedly. Wine output is:


I'm having the same problem here. I'm using Ubuntu 11.10 x64, wine 1.3.28 and Playonlinux 3.8.8

---

### Post by wild_oscar on 2011-12-28
I managed to make it work!

Roughly speaking, the steps were:

1) Install the game through Play on linux, as described in a previous post
2) Install the .4 patch through play on Linux
3) You can copy the custom .exe (which you'd gladly skip if they ever made a Linux version of the game); Don't copy any dll's
4) Run the game through the command line; before running the game, run the stress program to stress out your cpu
5) While the game is loading, vigorously move your mouse around (really! it's the same principle as the stress program)

---

### Post by byrom on 2012-01-13
I got FM 2012 running through this method but I have 2 minor problems.

The first one is I cannot for the life of me get Editor to run, it says couldn't find data folder etc. . The second is a minor mouse glitch in game, can be very irritating.

Any help would be GREATLY appreciated.

---

### Post by wild_oscar on 2012-01-13
Couldn't get the editor to work either. I'm editing in Windows, unfortunately.

---

### Post by radekz989 on 2012-01-25
Hello,
I did everything what was previously discussed, installed FM through PLayOnLinux and still got nothing.
FM eventually started but on the screen of "Loading" to the main menu, it crashed. Now, it doesnt even wanna do that.
Any help would be appreciated.
Wine output:

> radek@radek-Aspire-6930G:~/.PlayOnLinux/wineprefix/FM/drive_c/Program Files/Steam/SteamApps/common/football manager 2012$ wine fm.exe -openglerr:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:process:GetLogicalProcessorInformation (0x54f20a0,0x32fd88): stub
fixme:powrprof:GetActivePwrScheme (0x32fa6c) stub!
fixme:gameux:GameExplorerImpl_VerifyAccess (0x13bd08, L"Z:/home/radek/.PlayOnLinux/wineprefix/FM/drive_c/Program Files/Steam/SteamApps/common/football manager 2012/fm.exe", 0x32faf8)
fixme:userenv:RegisterGPNotification 0xb0 0
fixme:userenv:RegisterGPNotification 0xb4 1
fixme:nls:GetGeoInfoW -1 4 0x32eee0 3 0
fixme:nls:GetGeoInfoW -1 4 0x32f358 3 0
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x10076 0x00000000
fixme:win:EnumDisplayDevicesW ((null),0,0x6bee3dc,0x00000000), stub!
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x2007c 0x00000000
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d:wined3d_device_reset Cannot change the back buffer count yet.
fixme:d3d:wined3d_device_reset Cannot change the back buffer count yet.
fixme:d3d:wined3d_device_reset Cannot change the back buffer count yet.
fixme:win:EnumDisplayDevicesW ((null),0,0x6bedf48,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x6bedf48,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f3c8,0x00000000), stub!
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  135 (GLX)
  Minor opcode of failed request:  27 (X_GLXCreatePbuffer)
  Serial number of failed request:  3485
  Current serial number in output stream:  3486

---

### Post by Flegmatik on 2012-06-09
If you need help, there is a fansite exclusively focused Football Manager for linux : [http://www.fmtux.net/](http://www.fmtux.net/) The site is in french but in the menu you can easily translate it :)

---

### Post by luke91 on 2012-07-21
Awesome guide dude, cheers. Just one slight issue, when I start the game it says the graphics aren't good enough to support 3D games, and gets rid of windscreen (2 black bars down each side of my screen). Its not a massive issue, just wondered if anyone else had this or knows whats up. My laptop definitely can handle it as I've ran FM2012 on windows fine.

---

### Post by sombranegra79 on 2012-07-30
I don't have a CD, as I bought FM12 through the Steam online store. Any ideas how to get it to work?

---

### Post by ThunderSTM on 2012-08-16
Hi,
I have problem with 3D graphics. I have already ran FM12 and i can play it - it's working OK. but the game says that my graphic card cant support 3D matches and allows me to play only in 2D -  my card is good and in windows I was playing it without problems, but can you tell me how to configure it or what do I need to install to run 3D?
I have installed DirectX 9, .net framework 4.0, something called Video Driver from the PlayOnLinux Settings menu, configured the FM settings to OpenGL and other things and the result is the same - no 3D matches...
Please help!

---

