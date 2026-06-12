---
title: "Error with Talisman online"
date: 2007-12-01
forum: Wine
---

### Post by andvan on 2007-12-01
I am trying to play Talisman Online. When I load the game I get an error saying Startup engine [Ui] Failed.

This is what I get in the Terminal:
fixme:win:EnumDisplayDevicesW ((null),0,0x34f5b8,0x00000000), stub!
fixme:mmio:MMIO_InstallIOProc Global procedures not implemented
fixme:mmio:MMIO_InstallIOProc Global procedures not implemented
fixme:d3d8:ValidatePixelShader (0x2501708 (nil) 0 (nil)): stub

---

### Post by cogadh on 2007-12-01
The "fixme" messages are just developer notes about incomplete or unimplemented Wine functions. They generally mean nothing to an end user and most applications will still run despite them.

It might help to know a little about your system, specifically what video hardware do you have and have you installed the 3D accelerated drivers for it?

BTW - There is a Wine subforum now, all Wine related problems should be posted there. Expect the mods to move this thread over eventually.

---

