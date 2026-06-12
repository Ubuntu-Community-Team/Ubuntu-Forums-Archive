---
title: "Counter-Strike: Source with Ubuntu?"
date: 2007-08-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by AisDeck on 2007-08-17
Is it even possible? I've done everything they say in wine application database, and steam works just fine and even HL1 works fine, but when I start CS:S the screen looks first fine  and then it turns to this:
[http://wellfish.fi/~aisdeck/css.png](http://wellfish.fi/~aisdeck/css.png)

Font and background are all messed up, it's impossible to play. :(

Renderer problem?

---

### Post by acalafra on 2007-08-17
you have tahoma font right? i've gotten CS to be playable with wine and ubuntu. but i dont have source. i needed tahoma to get fonts to show up at all. then i got it and i had similarly garbled fonts. but i ended up getting it to the point where the font was still just readable and the game was very playable. i dont know how. here is how i launch CS 
sudo wine "c:\Program Files\Steam\Steam.exe" -applaunch 10 -heapsize 542000 -fullscreen

applaunch 10 is the code to regular CS.  heapsize is the ram size to allocate to steam. -fullscreen might be obsolete code. hope this helps. or maybe helps somebody who hasnt tried these yet.

---

### Post by afonic on 2007-08-18
CSS won't work good with wine, at least at my setup. However, using Cedega it works fine at DX8 mode (it selects that mode automatically).

Just make sure you have the "ia32-libs-sdl" package installed.

---

