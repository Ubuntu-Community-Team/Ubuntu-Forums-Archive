---
title: "Counter-Strike 1.6 Crashes with a Microsoft Visual C++ Library Error"
date: 2008-02-12
forum: Wine
---

### Post by canistra on 2008-02-12
Here is the otput:

```
fixme:win:EnumDisplayDevicesW ((null),0,0x33f618,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:shdocvw:ViewObject_SetAdvise (0x16b390)->(1 00000002 0x676588)
fixme:shdocvw:PersistStreamInit_InitNew (0x16b390)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x16b390)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x16b390)->(ffffffff)
fixme:winmm:MMDRV_Exit Closing while ll-driver open
```

---

### Post by SeanHodges on 2008-02-12
OK thanks.

---

### Post by BlueKoala on 2008-02-12
I would suggest to create a backup of config.cfg from you cstrike folder and then remvove/rename it. When starting CS1.6 it should re-write a new config file with all default settings. It may work for you.

---

### Post by canistra on 2008-02-13
> **BlueKoala said:**
> I would suggest to create a backup of config.cfg from you cstrike folder and then remvove/rename it. When starting CS1.6 it should re-write a new config file with all default settings. It may work for you.

that didn't helped :( any other sugesstions ?

---

### Post by BlueKoala on 2008-02-13
Ok, try running glxgears:
Open console:
Type: glxgears

Post the output.

Also, what video card are you using?
And what video driver are you using?
Are any other OpenGL games working?

Thanks

---

