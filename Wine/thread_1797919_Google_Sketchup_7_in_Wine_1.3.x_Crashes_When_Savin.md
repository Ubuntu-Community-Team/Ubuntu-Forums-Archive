---
title: "Google Sketchup 7 in Wine 1.3.x Crashes When Saving in Ubuntu 11.04"
date: 2011-07-05
forum: Wine
---

### Post by GenePayne on 2011-07-05
I used to run Google Sketchup 7 under Wine 1.3 in Ubuntu 10.04. Running Sketchup 7 in Wine 1.3.x is certified gold at winehq, and it worked without problems for me.

Now in Ubuntu 11.04, Sketchup still seems to work great for everything except saving the file I'm working on (of all things).
This has been replicated on two systems running Ubuntu 11.04. One of them 32-bit, the other 64-bit. Also one runs compiz, the other metacity for window management, so it isn't related to that.
Exact wine version is 1.3.15. Exact google sketchup version is 7.0.8657.

There is a workaround for this: in sketchup preferences, I set auto-save interval to 1 minute. This saves my work at this interval to the same directory as the file I opened. When I'm finished working and ready to quit sketchup, I have to wait one minute to make sure that the auto-save file has all of my changes. Then I go into the directory and make a copy of the auto-save file and rename it to whatever. Finally, I just quit sketchup (it then automatically deletes the auto-save file) and click no when it asks if I want to save the file (if I try to save, Sketchup crashes).

---

### Post by Tuffe Uffe on 2011-10-23
That's interesting. I have exactly the same problem, but for 10.04. I'm using an old version of Wine (1.2.2) since that's the newest one in the Ubuntu Software Center. 

I also have to make use of the auto-save function.

Has the problem been solved for you?

---

### Post by Tuffe Uffe on 2011-10-23
Now I know what the problem was... I first installed Google SketchUp 7.0.8657, but when I instead installed Google SketchUp 7.0.10247 it worked (I did not manage to uninstall the old version, so I just installed the new one on top).

Maybe that was the problem also for you?

---

### Post by GenePayne on 2011-10-25
Cool, thanks!

Yes, I was using version 7.0.8657. I upgraded to 7.10247 and it no longer has this problem.

---

