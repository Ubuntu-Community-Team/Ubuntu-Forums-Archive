---
title: "F.E.A.R. in Wine?"
date: 2008-03-28
forum: Wine
---

### Post by sudo panda on 2008-03-28
I've just installed F.E.A.R. using wine in my Ubuntu Gutsy.
But i can't get past the opening intro movies...:S
I'm able to play call of duty 4 alright on it, so i was wondering if anyone's got this game to work??
thanks for any help. :)

EDIT: And Yes, i have already read the WineDB for tips on installing it.

---

### Post by sudo panda on 2008-03-29
anyone?? :(

---

### Post by agtownz on 2008-03-30
F.E.A.R. is known not to work on Wine, last time I checked.  [http://appdb.winehq.org/objectManager.php?sClass=version&iId=5159&iTestingId=12223]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=5159&iTestingId=12223") shows some hacks to try.

---

### Post by sudo panda on 2008-03-30
1. Apply this patch and recompile wine
[http://www.winehq.org/pipermail/wine-patches/2008-March/051162.html](http://www.winehq.org/pipermail/wine-patches/2008-March/051162.html)
2. Install the game. If you can't enter cd key during the installation run regedit and change
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Hardware Profiles\Current\Software\Fonts\LogPixels
to smaller value
3. Put native dinput8.dll and d3dx9_36.dll to your game or system32 folder. Run winecfg and change dinput8 to native
4. Apply 1.08 patch(if you don't want to enjoy all the game bugs...)
5. Pixel Doubling and Soft Shadows won't work until you change
HKEY_CURRENT_USER\Software\Wine\Direct3D\OffscreenRenderingMode
to "fbo"

which part did you mean?

---

