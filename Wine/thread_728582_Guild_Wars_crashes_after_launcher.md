---
title: "Guild Wars crashes after launcher"
date: 2008-03-19
forum: Wine
---

### Post by ifflejink on 2008-03-19
So, after I run the Guild Wars launcher, which runs fine and downloads all the updates, the actual program stops on a black screen, although it does load the mouse, the mouse is movable, and only that one workspace is frozen. Guild Wars was running flawlessly for me a few weeks ago, then suddenly stopped; no updates, no changes. The terminal output is this:

fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x17d200) : stub
err:ntdll:RtlpWaitForCriticalSection section 0x7e626600 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 003b, blocked by 002c, retrying (60 sec)
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout (nil) is not supported
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:keyboard:X11DRV_MapVirtualKeyEx keyboard layout (nil) is not supported

So, does anyone have any idea what's going on?

---

