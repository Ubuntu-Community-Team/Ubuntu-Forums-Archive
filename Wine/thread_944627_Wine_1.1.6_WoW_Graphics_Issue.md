---
title: "Wine 1.1.6 WoW Graphics Issue"
date: 2008-10-11
forum: Wine
---

### Post by mrmagpie on 2008-10-11
I recently installed Wine 1.1.6 on my laptop, and now when I run World of Warcraft there seems to be some kind of graphics issue. The initial log-in screen opens, but the animation freezes and the screen greys in and out like my computer is having trouble running the application.

Has anyone else had this problem? And, as other people experiencing issues with 1.1.6 have asked, is there any way to roll back Wine to an earlier version?

Update: Fixed the problem myself. Don't know anything about computers, really, but what I did was go into Configure Wine and uncheck the Allow the window manager to... options.

---

### Post by kaminekosan on 2008-10-18
The solution in your update worked with my problem as well. 

I'm running Ubuntu Gutsy and Wine 1.0.

I was trying to update WoW with the new patch (2.4.3 to 3.0.2) but I encountered all sorts of problems. Mostly, the game would just freeze up and stop responding before the patch would have the opportunity to update the game. Or it would just run the donwloader (even though the patch was downloaded days before), check if all of the file was downloaded and after that shut down.

Unchecking all the "Allow window manager.." options solves this and everything worked out nicely. After the game was updated, I just checked the "Allow window manager.." boxes again and all was well :)

So thanks for the post update!

---

