---
title: "Portal crashes after splash screen."
date: 2008-10-04
forum: Wine
---

### Post by DOS4dinner on 2008-10-04
System: Pentium 4 2.6ghz, 1GB RAM, and 128mb ATI Radeon 9800 graphics card. Ubuntu 8.04, and Wine 1.1.5.

I set up Steam in accordance with the appdb entry, and I installed portal from the DVD retail release. Installation went perfectly.

Problem: After the valve/source logo screens, the mouse appears, the screen goes white, and the main menu music plays. Since there is no menu, it has to be killed manually.

I've tried:
Setting hl2.exe to Windows 98
Running it with this command:
wine steam -silent -applaunch 400 -window -novid -dxlevel 80 -width 1024 -height 768
Disabled in-game steam community.

While running, the game outputs a billion OPEN_GL_INVALID_ OPERATION errors to the terminal.

Other games I can run perfectly: Tribes, Defcon, Kid Mystic, Battlezone II.

fglrxinfo:

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 PRO
OpenGL version string: 2.1.7412 Release

Any Ideas? I just want to figure out if the cake really is a lie...
Thanks in advance!

---

### Post by jacksaff on 2008-10-04
Try -dxlevel 81 or 82 instead. dxlevel 80 caused huge grief on my pc.
I also found that once I'd launched it once I could get rid of the switch altogether. I had some missing sprites before and doing that made them all load for some reason.
Also probably better set as xp than 98 these days.
The cake is not a lie...

---

### Post by DOS4dinner on 2008-10-05
No...Still not working. Research states that Wine + Portal + ATI card = Disaster, at least from what it looks like on the AppDB entry. So far, it always ends up in the WSOD (White Screen of Death). Thanks for the help though.

---

