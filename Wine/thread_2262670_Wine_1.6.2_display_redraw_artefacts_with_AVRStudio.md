---
title: "Wine 1.6.2 display redraw artefacts with AVRStudio 4.18"
date: 2015-01-26
forum: Wine
---

### Post by tim222 on 2015-01-26
After successfully running AVRStudio 4.18 on various older wine releases, I've now updated to wine 1.6.2 and have a display issue.

The main editor pane in AVRStudio does not redraw properly, with some regions failing to redraw when the pane is scrolled or resized. This leaves a few holes in the display where the pane underneath can be seen, or when scrolling the window some artefacts of lines are left in place and not scrolled with the rest.

I'm using Ubuntu 14.04 with the open source graphics driver (the AMD driver no longer supports my X1200). The issue doesn't occur if I run wine 1.3.28 with the same .wine installation on the same system - please could someone advise on where I should look to fix this issue, or what has likely changed from 1.3.28 to 1.6.2 that affects screen redraw? Changing the supported Windows version makes no difference.

Thanks for your help!

Here the editor pane shows holes to the background and to the other panes in the stack:

[IMG]http://i7.photobucket.com/albums/y288/tim0123456789/Screenshotfrom2015-01-26182627.png[/IMG]

---

### Post by tim222 on 2015-01-26
Hmm, thinking about it, it's the <Tab> characters that are not redrawn and become transparent. <Space> characters are drawn properly. Any ideas? Thanks!

---

### Post by tim222 on 2015-02-01
OK, so this issue relates to gdi32.dll and was introduced with the changes from 1.5.19 (working) to 1.5.20 (not working). It looks like there were a few modifications to GetTextExtentExPointI in font.c that change the behaviour.

I have fixed it by compiling gdi32.dll with the older versions of driver.c, font.c, and freetype.c from version 1.5.19 (with corresponding change to the GetTextExtentExPoint function declarations in include/wine/gdi_driver.h). Maybe this breaks something else, I don't know, but AVRStudio now displays text correctly.

I have no knowledge of how gdi32.dll works, so I'll submit a bug report, but I don't know if this is a bug in wine or in AVRStudio.

[https://bugs.winehq.org/show_bug.cgi?id=37994](https://bugs.winehq.org/show_bug.cgi?id=37994)

---

