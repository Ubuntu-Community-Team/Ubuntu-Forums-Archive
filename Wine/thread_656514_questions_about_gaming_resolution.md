---
title: "questions about gaming resolution"
date: 2008-01-02
forum: Wine
---

### Post by thefatmoop on 2008-01-02
i installed wine, wine-doors, and cedega, but i'm unable to get the resultion to correct itself. Looks like i'm getting there, with steam working, warcraft3, starcraft, and sound working on all 3, but whenever i close starcraft or warcraft the resolution doesn't go back to 1280x800 @ 51 hz. 

i was trying to do a presentation with ubuntu a while ago, but  my laptop didn't like the projector. Under Administration > "Screens and graphics" the "gksu displayconfig-gtk" command isn't working since. i tried to copy it from the live cd and replace it under /usr/bin, but that didnt work either.  i'm guessing that's the default because when i login it's on a low resolution then it changes back to the resolution i want, after running a game outside of the 1280x800 it goes back.

any ideas? 

(and does anyone know how to get warcraft 3 working online?)

---

### Post by disturbedite on 2008-01-02
well, starcraft is so old it only supports very low resolutions, you can't force it to any others.

and iirc wc3 doesn't support widescreen resolutions....

---

### Post by thefatmoop on 2008-01-02
yeah it's fine if the game won't go to the lcd's proper resolution, but is there a way i can get the os to switch back to the proper resolution when i close the game?

---

### Post by disturbedite on 2008-01-03
ohhhh, yeah, that can be a problem for some ppl, fwik.  i had that problem for a while too but it was "fixed" somewhere along the line with a new version of wine.  (i don't know which one tho).
there are some solutions such as using a script to launch a game and then forcing x to revert to the desktop resolution.
there are prolly other solutions too.  (try searching this forum & looking at the app's winedb entry for solutions).
but after running games *x should* return to the desktop res, unless x or wine crashes.
sorry i can't give you any more info, but hopefully that will point you in the right direction.

---

