---
title: "VisualBoy Advance and Wine"
date: 2007-12-21
forum: Wine
---

### Post by joethepirate on 2007-12-21
Hi,
I'm a complete beginner in the world of Linux and until recently I have always used Vista. I must say, that so far I am enjoying Ubuntu a lot.

My question is:
Is it possible to get VisualBoy Advance to work with wine?

I realize that there are Linux versions of this game working already, but I do enjoy being able to input gameshark codes. There have been a few other threads started by people who would like to see this function running on the Linux based versions of VisualBoy Advance but so far they have gone unanswered.

It seems to me, if Wine allows windows based games to run on Linux, it should not take too much effort for the windows based VisualBoy Advance to run on Linux. This should allow for the input of gameshark cheats as well, correct?

Thank you, very much for your time. Any feedback at all would be helpful.

---

### Post by DoktorSeven on 2007-12-21
Windows VBA under Wine works fine here.  I had to set the renderer to OpenGL for it to display properly but it did fine after that.  There was a bit of problems with the menus showing up (they're there, but just obscured by the game; clicking where they should be will open one up).

---

### Post by disturbedite on 2007-12-21
i'm with you, i used a windows pc for this very reason last week to play a game...

shame the linux version doesn't have code support.  (at least the frontend/gui doesn't).

---

### Post by magicman692 on 2007-12-21
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3730&iTestingId=17055](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3730&iTestingId=17055)

^^^
It should work fine... maybe you dont have the latest wine version, 0.9.51?

---

### Post by joethepirate on 2007-12-21
Thanx for the feedback, guys. I just need to figure out how Wine works now.
:-D

---

### Post by joethepirate on 2007-12-21
Is there anyway, someone could outline the steps I would need to take to make VisualBoy Advance run with Wine?

Please keep in mind, that i am an absolute beginner.

Your help would be greatly appreciated.
Thank you.

EDIT

I get the following error when I try and run VisualBoyAdvance.exe with wine:

kunal@kunal-laptop:~/Desktop/VisualBoyAdvance-1.7.2$ wine VisualBoyAdvance.exe
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\home\\kunal\\Desktop\\VisualBoyAdvance-1.7.2\\VisualBoyAdvance.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\kunal\\Desktop\\VisualBoyAdvance-1.7.2\\VisualBoyAdvance.exe" failed, status c0000135

---

### Post by joethepirate on 2007-12-21
Hi,
After doing more research I have found that simply downloading mfc42.dll and putting it into my System32 folder in Wine has fixed the issue.

Thank you, everyone who responded.

---

### Post by Akira Takano on 2009-11-12
to all of you who are haveing trouble with windows programs, i recoment if you still have windows, to copy your system32 folder and past it in the system32 folder of wine. when it asks if you want to merge/replace, click the option allowing you to do so. this should solve most problems you may have with windows programs on ubuntu. at least it did for me. im running ubuntu9.10-karmic koala.

---

