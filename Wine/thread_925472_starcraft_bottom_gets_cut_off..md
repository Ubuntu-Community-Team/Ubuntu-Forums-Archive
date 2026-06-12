---
title: "starcraft bottom gets cut off."
date: 2008-09-20
forum: Wine
---

### Post by chrisruls00 on 2008-09-20
when I run starcraft the bottom part gets cut off. I tried a virtual desktop and it works, but I want to run it fullscreen. Is there anyway I can do this? It could be a problem with the resolution, I have my resolution set to 1024x768

---

### Post by Sugi on 2008-09-20
cam you upload a screen shot of starcraft in fullscreen mode?

and

try running starcraft through the terminal

env WINEPREFIX="/home/USR/.wine/" nice -20 wine "C:/Program Files/Starcraft/StarCraft.exe"

/USR/ as in your user name.

and copy the output of your terminal into here after you input that command.

Sugi

---

### Post by chrisruls00 on 2008-09-21
I'm running starcraft off of a flashdrive BTW. (So I can take it to school) I noticed today that I have the same problem with Diablo 2.

I get the following from a terminal:

```
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:winedevice:ServiceMain driver L"FileDisk" failed to load
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:advapi:SetSecurityInfo stub
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
fixme:win:EnumDisplayDevicesW ((null),0,0x7f21f428,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8

```

---

### Post by chrisruls00 on 2008-09-21
I fixed Diablo 2 by switching from 640x320(or something close to that) to 800x600. Is there a way you can do this with starcraft?

---

### Post by Sugi on 2008-09-22
You mean 640x480 for diablo 2?  I didn't even think Diablo 2 could go that small.

Starcraft's resolution is fixed at 640x480.  You can try to set it to that resolution.  It can not go any smaller or bigger.  I have made myself a portable version of starcrafts thanks to patch 1.15.2 and mpq.  I didn't have a problem with the portable version of starcraft.  You may need to export your rigestry from the original installation of starcraft.  Keep the export within the same directory of the portable starcraft and import to each computer it's used on.  That may fix the problem..

Good Luck,
Sugi

---

