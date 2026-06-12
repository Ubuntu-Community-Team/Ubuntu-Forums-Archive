---
title: "Rainbow 6 Vegas - wine"
date: 2007-10-08
forum: Wine
---

### Post by stonedwraith on 2007-10-08
I am trying to run Rainbow 6 Vegas using Wine 0.9.33

getting following error, any help would be appreciated.

fixme:thread:SetThreadIdealProcessor (0x10): stub
fixme:thread:SetThreadIdealProcessor (0x2d0): stub
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x6c70020) : stub, simulating 64MB for now, returning 64MB left
fixme:thread:SetThreadIdealProcessor (0x2f4): stub
err:dsound:DSOUND_MixOne underrun on sound buffer 0x206c98
fixme:winmm:MMDRV_Exit Closing while ll-driver open

---

### Post by cogadh on 2007-10-08
R6V doesn't work in Wine:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=8149](http://appdb.winehq.org/objectManager.php?sClass=version&iId=8149)

However, the last Wine version it was tested with was 0.9.44, so you might want to try updating to the latest Wine, 0.9.46, and test it yourself.

EDIT - NVM, I didn't realize that R6V requires multi threaded D3D and Shader Model 3.0, neither of which work in Wine (yet). There is some info on that AppDB page that may explain how to disable SM 3.0 in the game, but it is still unlikely to work without functional multi threaded D3D support.

---

