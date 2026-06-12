---
title: "Portal (portals make the screen go black)"
date: 2008-06-28
forum: Wine
---

### Post by greggatghc on 2008-06-28
Ive tried all the tricks I can find in here.  Everything seems to look ok now.  But once it gets to the countdown for the first portals to appear it goes 3 2 1 then black screen.  I can hit the escape key and get the menu up and exit.  

Here is how I start it:
env WINEPREFIX="/home/gregg/.wine" WINEDEBUG="fixme-all" wine "C:\Program Files\Steam\steam.exe" -applaunch 400 -heapsize 512000 +map_background none -window -dxlevel 81 +mat_forcehardwaresync 0

(got most of that from various threads on here)

---

