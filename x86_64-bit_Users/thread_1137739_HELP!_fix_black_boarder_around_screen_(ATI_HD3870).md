---
title: "HELP! fix black boarder around screen (ATI HD3870)"
date: 2009-04-25
forum: x86 64-bit Users
---

### Post by Ferrar2992 on 2009-04-25
hi i just installed the latest ati drivers from thier website but after i rebooted i got this black boarder aroung my screen! i have it connected throug  DVI/HDMI to my Samsung LCD 1080p. before installing the drivers i had a full screen! anyone know how to fix this??

---

### Post by nikgare on 2009-04-26
Whats wrong with the lastest drivers via the normal Ubuntu repos - they will surely funtion better with Ubuntu?

---

### Post by shabazzk on 2009-05-06
1. Go to Applications > Accessories > ATi Catalyst Control Center
2. Expand Displays click your display, it should read HDTV or DTV(1)
3. Click the Adjustments tab and set "Scaling Options" slider to 0.

Your desktop should now fill the screen.

For some reason the screen is scaled back for HDMI in ATi 9.4 driver.

I've had this problem for a week, but did nothing about it in Ubuntu, then I installed Widows 7 on the same machine, and had the same problem in windows 7. Searching through the Catalyst settings in advanced mode, I found this setting. Sure enough, setting it to 0 in Windows 7, also solved the problem. Not sure why this is the default in the driver, but it's annoying.

Why install  ATi proprietary drivers instead of the open source ones?
You need the drivers from ATi's site if you want better 3D support.

---

