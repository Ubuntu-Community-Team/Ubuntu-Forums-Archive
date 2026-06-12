---
title: "brothers in arms under wine"
date: 2007-10-29
forum: Wine
---

### Post by pondochris on 2007-10-29
I just bought brothers in arms road to hill 30 and figured I would give it a go with wine. Everything installed and starts up flawlessly(I'm still amazed)! However I can only look 180 degrees. I should be able to keep turning till I get dizzy. When I reach the point where I can no longer turn, my standard cursor appears as if I'm reaching the edge of the window. I fiddled with some wine settings but couldn't fix it.I'm thinking that there's some setting I need to change in order to not reach the edge of the window.   Could anyone offer some insight?
I'm running 64 bit gutsy on amd 64x2 6000 with onboard nvidia 6100 128MB graphics. Its a fresh install and I installed wine with apt. Thanks in advance.

---

### Post by cogadh on 2007-10-29
There is a known bug in Wine's implementation of DirectInput that produces symptoms like this. It is likely what is causing your problem and has already been reported as an issue with BiA:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=6335](http://appdb.winehq.org/objectManager.php?sClass=version&iId=6335)

---

