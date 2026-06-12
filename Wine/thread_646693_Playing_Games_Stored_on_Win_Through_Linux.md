---
title: "Playing Games Stored on Win Through Linux"
date: 2007-12-21
forum: Wine
---

### Post by ExSuSEusr on 2007-12-21
Hey everyone...

Got a question here...

Say you got a few games stored on a Windows partition that you want to play through Ubuntu. 

Any software apps make this possible?

No wine wont work - one of the games is Everquest.  Cedega not doing well with it either.

---

### Post by cogadh on 2007-12-21
No it is not possible to do that. The only tools that allow you to run Windows applications in Linux are Wine, CrossOver and Cedega. None of them will work properly if you try to use them to run games from a Windows partition, they only really work if you install the game into Linux. However, you can set up the games to use the same save files in Windows and Linux by symlinking the save directory in Linux to the save directory in Windows.

---

### Post by vek on 2007-12-21
I have had (limited) success in using the same games via WINE - by symlinking their folders into my WINE's fake-windows drive somewhere.  It shows up as drive C, afaik, so if the game is also installed in drive c on windows, and the path is the same, I find that the chances improve.

this does NOT work with steam, unfortunately, else I'd save a heap of space for team fortress 2.  And games which rely heavily on shared libraries / dlls placed in the windows folder / registry keys installed / etc tend to fail.  Although you can try first symlinking the folder, then installing it "over itself" to make sure both environments have the necessary dlls and things.

All experimental, all risky :P

---

