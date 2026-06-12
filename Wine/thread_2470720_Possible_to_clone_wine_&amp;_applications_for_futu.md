---
title: "Possible to clone wine &amp; applications for future installations?"
date: 2022-01-08
forum: Wine
---

### Post by DVD-R on 2022-01-08
Hello all,
Is it possible to clone wine and any installed applications in a Ubuntu PC and save it.
And then use that within another Ubuntu PC in the future?

Thanks in advance!

---

### Post by TheFu on 2022-01-09
Since nobody has answered ... WINE uses something called a WINEPREFIX environment variable.  This is commonly modified to have different locations on disk used by different Windows programs that need different WINE settings.  This would be where I started when looking for a way to copy an install.

However, the actual WINE program installed would be per distribution, so you'd need to take steps to get exactly that version.  A flatpak or snap should work for the next few years, provided you blocked any automatic updates.  Snap packages auto-update.  If not using snaps, but rather using normal canonical repo files, then use apt-mark to "hold" a specific version of WINE.  This will likely break some dependencies in 6+ months, since holding that package will cascade into other packages being held.  Eventually, the entire system will be in "package manager hell".  That's fine, if the entire purpose for the system is to only run WINE programs.

But software is always moving for a variety of reasons, some very important (security) and some frivolous (the NEW).

When I search my system for "wine", lots of locations are found.  Looks like the entire HOME directory for the userid should be backed up, since WINE puts files not just in ~/.wine/ but in ~/.local/share/ and  ~/.config/menus/ ... too.

All the stuff for wine that is system related seems to be part of the wine packages.  I know through experience that different versions of WINE sometimes break previously working setups.

Hope this helps.

Maybe the best solution is to get a separate HDD/SSD and use that for the entire OS?  Perhaps a SATA SSD in an external USB3.2 enclosure? That should provide more than enough speed and convenience for wine stuff. A 100G or 250G SSD should be more than enough, depending on the software.

---

### Post by DVD-R on 2022-01-10
Wonderful!
Thank you so very much for that every extensive answer!!!

That gives me a lot to go on - and how to make a decision moving forward.
I totally appreciate.

---

