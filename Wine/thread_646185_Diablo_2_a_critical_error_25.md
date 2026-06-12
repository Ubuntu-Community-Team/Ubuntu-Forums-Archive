---
title: "Diablo 2 a critical error 25"
date: 2007-12-20
forum: Wine
---

### Post by Arveician on 2007-12-20
DIablo will run just fine in window mode in direct draw, but when I try to run full screen I get this error.

Error 25: A critical error has occurred while intializing direct draw.

Here is my terminal launch 

 wine "C:\Program Files\Diablo II\Diablo II.exe" 
fixme:mixer:ALSA_MixerInit No master control found on MPU-401 UART, disabling mixer
err:aspi:SCSI_OpenDevice Failed to open device /dev/hdc: Read-only file system
err:aspi:SCSI_OpenDevice Failed to open device /dev/sg0: Permission denied
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:SetSystemCursor (0x111e,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1126,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f03),stub!
fixme:cursor:SetSystemCursor (0x113e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f02),stub!
fixme:advapi:SetSecurityInfo stub
spacedust@D-N-A:~$ fixme:win:EnumDisplayDevicesW ((null),0,0x81775c,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?

Ok for some reason my screen resolution is getting locked up. When I go to menu and change the resolution it will not change, until I log out and back in.
Once this is done, it some how unlocks it. Then wine is able to change my resolutions and all works again. So why is my screen resolution locking up?

---

