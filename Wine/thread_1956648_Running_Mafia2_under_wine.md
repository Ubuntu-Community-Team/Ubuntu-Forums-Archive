---
title: "Running Mafia2 under wine"
date: 2012-04-11
forum: Wine
---

### Post by rollcast on 2012-04-11
I've installed Mafia2 under wine and have got through the installer ok but when I try to run it I get the following in the terminal.

```
main@Presario-CQ56-Notebook-PC:~/.wine/drive_c/Program Files/2K Games/Mafia II$ wine launcher.exe -opengl
fixme:ntoskrnl:KeInitializeTimerEx stub: 0x111038 0
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:userenv:GetUserProfileDirectoryA 0xdc 0x33f167 0x33f16c
fixme:userenv:GetUserProfileDirectoryA 0xdc 0x3e4a40 0x33f16c
fixme:win:EnumDisplayDevicesW ((null),0,0x33df28,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33e234,0x00000000), stub!
Failed to load ADL library
fixme:wtsapi:WTSRegisterSessionNotification Stub 0x20064 0x00000000
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d:debug_d3dformat Unrecognized 875710020 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:getFormatDescEntry Can't find format unrecognized(875710020) in the format lookup table
fixme:win:EnumDisplayDevicesW ((null),0,0x33edc4,0x00000000), stub!
wine: Unhandled page fault on write access to 0xbfe17414 at address 0x738cbde4 (thread 0023), starting debugger...
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7ef811ca

```

---

### Post by rollcast on 2012-04-12
I upgraded Wine to version 1.3.28 and now the game will run but the graphics are very jumpy and there are rendering issues (some of the texture maps aren't right and the mouse jumps around quite badly)

---

### Post by ergo-proxy on 2012-04-12
The game has bronze rating so don't expect too much [http://appdb.winehq.org/objectManager.php?sClass=version&iId=21257](http://appdb.winehq.org/objectManager.php?sClass=version&iId=21257)

---

