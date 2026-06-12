---
title: "[SOLVED] Error Installing Fallout 2"
date: 2008-01-12
forum: Wine
---

### Post by sirdork on 2008-01-12
Help please me.  I keep getting an error when i run the setup.exe .  My wine is version wine-0.9.46 in win98 mode.
when I run setup.exe it says. " Error Initializing Video Mode".

Please help me.

---

### Post by sirdork on 2008-01-13
upgraded Wine to 0.9.53 but still same problem

---

### Post by MaximB on 2008-04-01
I got the same problem, the output :

```
maxim@maxim-ubuntu:~/maxddark/games/fallout2install$ wine SETUP.EXE 
fixme:spoolsv:serv_main (0 (nil))
err:service:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
fixme:win:EnumDisplayDevicesW ((null),0,0x34efb4,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3512
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 8
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?
```

Using Ubuntu Gibbon and Wine 0.9.58

---

### Post by Zophixan on 2008-04-02
Hey, I have this problem too, how did you solve it?

---

