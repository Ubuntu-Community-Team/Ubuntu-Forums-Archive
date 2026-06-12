---
title: "(Puppy Dingo) Wine and AOE II Configuration Questions"
date: 2008-09-21
forum: Wine
---

### Post by BEND IT 7 on 2008-09-21
I recently setup Puppy Dingo on an ancient laptop for someone else, and I have been impressed by the performance, which, although slow, is about as much as we can ask for on a 96mb 4 gig HD and super slow processing laptop.  I am also an avid Ubuntu user (on my laptop). 

Anyway, I configured Wine successfully and got Age of Empires II fully installed (and the no-CD patch so it can be played on multiple computers and to compensate for the poor CD reading ability of the laptop). When I went to play it, it started to load but then it said something like, "Error: The graphics card is not DirectDraw capable." I was wondering if there is any feasible way to fix this problem. I know it could actually just be an error because the graphics card is truly to old to run Age of Empires, but I was wondering if anyone had any suggestions before I uninstall everything.

---

### Post by pytheas22 on 2008-09-21
On a machine that old, it could indeed be the case that the video card is just too old.  But do you know the name of the card?  If not, run the command:
```

lspci
```

and you should see an entry pertaining to your graphics card that will hopefully tell you the name and model.  Maybe (but not necessarily) if you google around you can figure out whether it's supposed to support direct-draw or not.

I'm guessing it doesn't if wine says it doesn't, but you might as well try.

---

