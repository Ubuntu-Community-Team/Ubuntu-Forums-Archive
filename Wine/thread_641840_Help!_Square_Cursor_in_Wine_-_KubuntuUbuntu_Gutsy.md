---
title: "Help! Square Cursor in Wine - Kubuntu/Ubuntu Gutsy"
date: 2007-12-15
forum: Wine
---

### Post by jdlongmire on 2007-12-15
I have not seen this in any WIne install on Kubuntu - done it about 5 times with Gutsy - but my mouse arrow is this .5"x.5" square box with black and white alternating lines. The upper right corner of the box works as the arrow tip, but it is very distracting - any help?

I have been ALL OVER google - no joy :(

---

### Post by hikaricore on 2007-12-15
Sounds like a video driver/hardware issue.

You should list your hardware here and what drivers you have installed
You may also want to mention the game/software title you're experiencing this with.

---

### Post by AndrewRiedi on 2007-12-20
What application does this happen in?  Winecfg? All applications?

Are you using Xcursor?

Can you post a +cursor log?
WINEDEBUG=+cursor wine prog.exe &> ~/Desktop/cursor.log

What version of Wine?
wine --version

Self-compiled?  Or a package?  Custom patches?

What cursor icon should be showing?  IDC_ARROW (The standard arrow cursor)

Does this happen for eg. IDC_IBEAM (The text cursor.  Testable in winecfg with a textbox on the "Drives" tab.)

---

