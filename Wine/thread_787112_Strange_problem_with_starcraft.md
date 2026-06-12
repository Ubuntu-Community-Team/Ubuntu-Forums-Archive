---
title: "Strange problem with starcraft"
date: 2008-05-08
forum: Wine
---

### Post by olskar on 2008-05-08
Hi, I get this strange videoproblem with starcraft. I dont know if the output is relevant?



preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
preloader: Warning: failed to reserve range 00000000-00010000
fixme:advapi:SetSecurityInfo stub
preloader: Warning: failed to reserve range 00000000-00010000
fixme:win:EnumDisplayDevicesW ((null),0,0x32f410,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3518
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8

---

### Post by Forged on 2008-05-10
trying running it in opengl instead of directx

open a terminal and go to the starcraft directory then

```

wine starcraft.exe(or w/e the exe file is called) -opengl

```

I had the same problem with warcraft 3 and that worked for me.

---

