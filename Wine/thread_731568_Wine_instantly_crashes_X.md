---
title: "Wine instantly crashes X"
date: 2008-03-22
forum: Wine
---

### Post by walkeraj on 2008-03-22
Okay, so I've done the requisite searching around, and I'm either missing something unbelievably simple, or something funny is going on here.

I'm attempting to run a couple of simple games under Wine 0.9.57 in Gutsy on my new System76 laptop.  When I attempt to run either of them, the loading graphic comes up, but the moment they attempt to change to fullscreen, X crashes.  No warnings, no output to the terminal, just a brief flash back to a text terminal and then right back to GDM.

So, it's obviously something video related, yet I'm rather surprised X is dying so fantastically in this way.  Could the fact that it's a widescreen resolution have something to do with it?  How should I begin to diagnose this problem?

System: System 76 Darter Ultra (Asus-built?)

Processor: Core 2 Duo T7700 2.4 GHz 800 MHz FSB 4 MB L2
Memory: 2 x 2 GB DDR2 667 MHZ
Display: 12.1" WXGA (1280 x 800)
Graphics: Intel GMA X3100
Audio: Realtek ALC 883H

EDIT:

Something else that's strange.  I've unpacked both of these games into ~/.wine/drive_c/games/<gamedir>, but when I attempt to run either of them, files are copied from <gamedir> into my home directory.  In the case of one game (called "La Mulana"), it is a .ini file.  In the case of the other, it is two .dlls and an .xm music file that the game plays.  This would seem to indicate these files are being copied as they are accessed.  Any ideas what's going on here??

---

