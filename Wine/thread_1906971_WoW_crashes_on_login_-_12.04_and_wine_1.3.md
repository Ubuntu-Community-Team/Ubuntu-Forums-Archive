---
title: "WoW crashes on login - 12.04 and wine 1.3"
date: 2012-01-10
forum: Wine
---

### Post by t.rei on 2012-01-10
I'm getting a bad file descriptor error every time I try to login to WoW on wine after upgrading to precise. 

Tried all combinations of wine1.3 from repos or launchpad and nvidia-current and nvidia-current-updates.

deleted wine directory and reinitialized

chowned all of the Warcraft directory

I'm out of ideas. And google doesn't help at all. Maybe anyone here knows something, that would be awesome.

Thanks.

---

### Post by tersogar on 2012-01-10
Try to go to c in wine and open wow.exe. This is only a work around but it help me.

---

### Post by t.rei on 2012-01-10
Cool - that seems to work. Now to find the reason:

If I launch wow with my command placed in /usr/local/bin/

wine explorer /desktop=0,1920x1200 "/home/username/.wine/drive_c/Programme/World of Warcraft/Wow.exe" -opengl

it crashed.

If I cd into the directory and run wine Wow.exe - it works. (only two-screen-mode is screwed up without the /dektop, but now I have a point from where I can try to fiddle)

*edit* and there we go - even if just adding the /desktop part, it does crash again.

*edit2* and as soon as I remove the /desktop part from the launchscript, wow starts fine again. So I guess thats where something changed.

---

