---
title: "Heavy CPU useage, Laggy"
date: 2009-10-01
forum: x86 64-bit Users
---

### Post by MaaaTtY on 2009-10-01
Hey many many times now i have noticed my CPU useage randomly jump up to about 40% and hardly move from there and it will not go back down unless i restart my PC.  It may have something to do with wine, but i cant remember what or when it triggered the last times this has happened but i will pay attention from now on.

Extra info: nothing like this happens on other OS's and i have a very good computer that i just built a few months ago.

---

### Post by dummy910 on 2009-10-01
```
top
``` into a terminal will show you what's going on in the resource department on that machine, OR in Gnome you can go System>Administration>System Monitor for a gui of the same info...

---

### Post by MaaaTtY on 2009-10-01
oh ya i forgot that i checked this already and the strange thing was nothing listed there was taking up and CPU.  All processes were basically 0%.  so it wasnt like i could kill the thing causing it.  now im not sure how wine works but thinking about it now wouldnt that be an indication that it is indeed wine because the applications i run from it may not be running in the process list (i will have to confirm this).

---

### Post by dummy910 on 2009-10-01
In the gui prog(System Monitor) the wine processes WILL show... just look for anything that has an .exe at the end of the name(explorer.exe, wine-services.exe etc).

---

### Post by MaaaTtY on 2009-10-01
i dont really mean wine itself i was meant more likely one of the programs i was running from it (only one last time it happened which was "Steam").

---

### Post by dummy910 on 2009-10-01
> i dont really mean wine itself i was meant more likely one of the programs i was running from it (only one last time it happened which was "Steam").
Again:
_any-all windows programs you run in wine will show in **System-Monitor** with an .exe(or .com...) at the end of the process name_. 

I don't have wine installed on this laptop I'm posting on, or I would include a screen-shot here to show you an outline, so maybe another fellow Ubuntu user could post one here...

---

### Post by MaaaTtY on 2009-10-02
oh, well either way nothing shows up with a high CPU useage and it just happened again but this time i was running nothing but "Display" and "update Manager".  it seemed to spike right when i was launching the 'Display' window.  But this time after things got laggy i waited a while and came back about 5-10 mins later and things were back to normal.

---

