---
title: "Wine programs pause 30 seconds on startup"
date: 2008-05-21
forum: Wine
---

### Post by kosmos on 2008-05-21
I'm running wine-0.9.59 under Gutsy on my AMD64 system, and every time I start a wine program it pauses 30 seconds before the program runs. This problem did not happen when I used 0.9.58, but I think I did see it before in some version prior to that.

Does anyone know how I can fix this?
Thanks.

---

### Post by Coolit on 2008-05-21
I have the same problem with certain apps after I upgraded to rc1, unfortunatly I dont know how to fix it either.

---

### Post by kosmos on 2008-05-21
Well, I guess it's good to know that I'm not the only one :)

A little bit more info: I believe the pause for wine to start is always 30 seconds, exactly. And there is no CPU usage, so it looks like it's timing out waiting for something. I just don't know what.

---

### Post by kosmos on 2008-05-21
Well, I think I sort of know what the problem was and what a general solution is.

The problem apparently was that there was an application that was either installed incorrectly, or uninstalled incorrectly that was trying to run on wine boot. Probably some bogus registry entry, but I wouldn't know how to figure that mess out.

I reinstalled wine and my application to a new WINEPREFIX and the problem is no longer there.

---

