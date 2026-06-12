---
title: "Playing WoW in Windowed Mode"
date: 2008-03-27
forum: Wine
---

### Post by bakentake on 2008-03-27
Okay so my problem is that whenever I open wow it shrinks my resolution from 1280x1024 to 1024x768, not much of a problem normally but in full screen several buttons are hidden under the top and bottom bars. And to tell the truth I'd rather run wow in a window at a resolution of 1024x768 so that I can still see my other windows without much trouble at all. But whenever I go into options and change to windows mode or change the resolution wow crashes and gives me an error:

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\WoW.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:02A00056

The instruction at "0x02A00056" referenced memory at "0x04AF002C".
The memory could not be "written".


For those who don't want to read all that:
Want to run wow in windowed mode at 1024x768 resolution while keeping my computer running at 1280x1024 resolution, but every time I try I get an error.

Thanks for anyone who has a solution. Also I'm u sing wine 9.58 , running as Windows XP.

---

### Post by bakentake on 2008-03-27
Okay I found out what I missed.

Going to config.wtf and typing several lines to it then after trying to go into windows mode it worked, the lines I added were:

SET gxApi "opengl"
SET Sound_SoundOutputSystem "1"
SET Sound_SoundBufferSize "150"

---

### Post by Hairy_Palms on 2008-03-27
rgw gxapi one would be what fixed it, otherwise wow uses direct3d, which is slower and buggy.

---

