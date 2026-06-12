---
title: "Alpha Flash 10 64-bit"
date: 2008-11-24
forum: x86 64-bit Users
---

### Post by DragonVengeance on 2008-11-24
So for over a year now I've been using 64-bit Ubuntu, with serious problems running any flash...flash will run for a few minutes then shut off, with the only solution to be to restart firefox...

recently I have noticed that a new Alpha Flash was available for 64-bit systems which claims to have greatly fixed a lot of those flash problems...

the thing about it is, in some ways it has...and in some ways it has made it much much worse...

youtube.com now works more perfectly than i have ever seen it before...however EVERY OTHER site with flash crashes on me (segmentation fault (core dumped)) [examples include espn.com, meebo.com, etc.]

i know there's bugs or whatnot from it being an alpha version and all, but i have yet to hear any negative reviews on this new player on these forums

(libflashplayer.so)

anyways, bottom line...anyone else have any problems with this new player?

---

### Post by Tiftof on 2008-11-24
same problem here: youtube works fine, every other site containing flash makes firefox crash...

Haven't found a solution yet

---

### Post by Thelasko on 2008-11-24
[File a bug report.]("http://bugs.adobe.com/flashplayer/")

---

### Post by Arup on 2008-11-24
No crashes here with any flash sites, be it on FF or Opera. Segmentation faults could come from improperly removed older x32 flash as well as nsplugins, these have to be removed thoroughly.

---

### Post by istblacken on 2008-11-25
have you uninstalled nspluginwrapper because it causes the segmentation fault. i tried that site you mentioned and they work properly. actually i haven t had any issues with flash x64 alpha.

---

### Post by Tiftof on 2008-11-25
nspluginwrapper isn't installed and no other libflash files on my system, only the x64 version in /usr/lib/firefox-addons/plugins/

I doubt it is a problem with firefox using some 32bit version or nspluginwrapper because youtube works fine

---

### Post by Bucky Ball on 2008-11-25
You need to completely remove the 32bit version, as mentioned.

---

### Post by felker2 on 2008-11-25
I run 64-bit Ubuntu, with flash from the Ubuntu repositories (thus 32-bit flash?), without any problems at all.

I'll start using the 64-bit flash as soons as it's part of the Ubuntu repository; I don't like to play with my system with other ways of installing software.

---

### Post by Kilz on 2008-11-25
> **felker2 said:**
> I run 64-bit Ubuntu, with flash from the Ubuntu repositories (thus 32-bit flash?), without any problems at all.

I'll start using the 64-bit flash as soons as it's part of the Ubuntu repository; I don't like to play with my system with other ways of installing software.

A very smart idea. Its an [COLOR="Red"]**ALPHA**[/COLOR]. Those that have little tolerance for problems or have flash working ok should leave this alone at lest til it gets closer to release.

---

