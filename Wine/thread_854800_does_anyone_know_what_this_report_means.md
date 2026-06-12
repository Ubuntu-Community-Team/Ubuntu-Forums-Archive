---
title: "does anyone know what this report means?"
date: 2008-07-09
forum: Wine
---

### Post by Meow27 on 2008-07-09
```
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
wine: Unhandled page fault on read access to 0x00000000 at address 0x401491 (thread 001c), starting debugger...
username@Frozen-Box:~$ fixme:winmm:MMDRV_Exit Closing while ll-driver open
```

aside from not being able to run this program (navyfield) in 32 bits i have come to this problem here

(i implanted a couple of dlls that are required to run this so you wont get the same report unless the necessary dlls are in your sytem32 folder in wine)
can someone tell me what this means please?

---

