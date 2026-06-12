---
title: "Company of Heroes Gold Edition CD doesn't work"
date: 2013-11-11
forum: Wine
---

### Post by W-Unit on 2013-11-11
Hi there.

I'm trying to install Company of Heroes Gold Edition from the CD using WINE.



I insert the CD, navigate to the optical drive in Dolphin, right-click on **Launch.exe**, and choose **Open With ... -> Wine Windows Program Loader**. See "CoHInstScr1.png" (attached) for what I see once I do this.
I then choose "Install." For a brief moment there is a very small dialog window that says "Designed with DemoShield."
Then I get "CoHInstErr-1.png" which says something about a problem with GameInst.exe, possibly due to a "problem in the program" or a "deficiency in wine."

This is the directory contents of the CD:
```
will@will-01:/media/will/Disk1$ ls -l
total 43087
-r-------- 1 will will 23402288 Jan  3  2008 AcroSetup.exe
-r-------- 1 will will   649428 Jan 15  2008 Autorun.dbd
-r-------- 1 will will       44 Jan  3  2008 autorun.inf
-r-------- 1 will will     4274 Jan  3  2008 Autorun.txt
dr-x------ 1 will will    53248 Feb 14  2008 Data
-r-------- 1 will will   528384 Jan  3  2008 demo32.exe
-r-------- 1 will will    22595 Feb 12  2008 EULA.txt
-r-------- 1 will will 14051208 Feb 14  2008 gameInst.exe
-r-------- 1 will will      390 Jan  3  2008 gameInst.exe.manifest
-r-------- 1 will will  1645320 Jan  3  2008 gdiplus.dll
-r-------- 1 will will   746816 Feb 14  2008 InstallerLib.dll
-r-------- 1 will will   132416 Feb 14  2008 Launch.exe
-r-------- 1 will will      367 Jan  3  2008 Launch.ini
-r-------- 1 will will       24 Feb 14  2008 Locale.ini
-r-------- 1 will will  2732818 Jan  3  2008 Manual.pdf
-r-------- 1 will will    46867 Feb 12  2008 Readme.txt
-r-------- 1 will will    99648 Feb 14  2008 Setup.exe
-r-------- 1 will will      298 Jan  3  2008 styles.css
```

The exact same error is reproducible if I choose to try running "Setup.exe" or "gameInst.exe" instead of "Launch.exe"
demo32.exe and AcroSetup.exe appear to work fine.

I notice on WineHQ, the rating for the "Steam Version" of CoH Gold Edition is "Gold." However, obviously, I am not using the Steam version... I've never run this particular game through Steam before, and I have installed it many times before (though always on Windows), so I know that Steam is not necessary to be able to play the game online.

Anyhow, thanks for your time and any help you can provide! :D

I love this game and haven't played it in forever....

---

