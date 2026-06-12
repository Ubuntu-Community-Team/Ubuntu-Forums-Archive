---
title: "Losing keyboard in Wine"
date: 2008-11-01
forum: Wine
---

### Post by hcaleman on 2008-11-01
I have problem with all wine apps (using wine 1.0), it will lose keyboard recognition after 1 character is typed.  I'm using a wireless keyboard (and mouse) if that has any effect.  The mouse however always seems to work fine.  

Currently happens regularly with both winecfg and fallout2.  Any ideas?

---

### Post by hcaleman on 2008-11-03
Bump and update.  Updated to wine 1.1.7, problem still exists (not much of an update I suppose). 

Terminal output: 
fixme:font:WineEngCreateFontInstance Untranslated charset 228
fixme:win:EnumDisplayDevicesW ((null),0,0x32f190,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 8
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(640,480)

---

