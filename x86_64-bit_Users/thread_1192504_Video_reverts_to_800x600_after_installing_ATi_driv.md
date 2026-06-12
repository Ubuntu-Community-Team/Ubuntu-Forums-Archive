---
title: "Video reverts to 800x600 after installing ATi drivers"
date: 2009-06-20
forum: x86 64-bit Users
---

### Post by Th3_uN1Qu3 on 2009-06-20
Of course i had to run into another issue. For some reason, after a second reboot the resolution went crazy. It goes to 800x600, most of the desktop chopped off, so i believe it's doing some kind of "virtual desktop". In display properties the resolution is still set to 1280x800. I have to switch to a different resolution then back to 1280x800 for my display to work properly, also it shows as "Unknown display". What can i do about it? I see xorg.conf editing does not work anymore.

Things i have tried: Reinstalled xorg -> good display, appears as laptop display 15", but no acceleration. Reinstalled ATi drivers -> acceleration works, but resolution reverts to 800x600 and display appears as "unknown". At least i am able to switch it back, but it's still very annoying. Any solutions please?

HP DV5: Athlon X2 2GHz, 2GB RAM, HD3450 512MB.

---

### Post by Th3_uN1Qu3 on 2009-06-21
Never mind, updating the ATi drivers to the latest version directly from AMD fixed it, and also solved the issues i had with Compiz - it now no longer disturbs other OpenGL apps.

---

