---
title: "ChemSketch 11 under wine 1.0"
date: 2008-09-27
forum: Wine
---

### Post by evillan on 2008-09-27
I'm trying to get ChemSketch 11 to work under wine 1.0.

According to [http://appdb.winehq.org/objectManager.php?sClass=version&iId=5846&iTestingId=13851](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5846&iTestingId=13851) I should
> mxsml bug in wine 0.9.26
by Jan Schiefer on Tuesday November 28th 2006, 10:18
Because of bug 6761 you need to disable the builtin msxml3.dll if you are using wine 0.9.26 or later.
If you don't it will crash at startup.

But that's from 2006. I tried it; didn't work. Does anybody know a workaround?

---

### Post by krazyd on 2008-09-27
have you tried using the latest development version of wine? for instructions see the winehq.org page.

---

### Post by DrScum on 2009-05-26
I just installed ChemSketch 12 and it runs under wine 1.0 with the following glitches:
-in order to make use of the 3D viewer you have to safe your structure as a .mol file and open that in 3D viewer
-in order to have it run normally the second time and all future times also you have to do the following

BEGIN QUOTE from: [http://en.opensuse.org/Wine](http://en.opensuse.org/Wine)
ChemSketch (version 12 and before) has had a windowing bug which means some WINE versions run it, and some do not (after the first initialisation when a registry entry is made that has the effect of making the ChemSketch window invisible after start up on all future start ups. The clean solution is to run a start up line like wine start /MAX 'C:\windows\temp\ACDFREE12\CHEMSK.EXE' which forces the window size and then adjust the size of the ChemSketch drawing document. You have to save a *.mol file to disk and reopen it to get 3D molecular displays.
END QUOTE 

The windowing bug also seems to apply to the 3D viewer, i.e. you have to start the 3D viewer from the command line also. If you start it from within the Chemsketch application it works only the first time.

Another problem seems to be the fact that you can't copy/paste structures and 3D pictures by using the clipboard, but that's a problem that the windows version has also. The Chemsketch graphics format doesn't seem to be compatible with OpenOffice. You have to save as a bitmap first and then import into the OpenOffice.

If anyone could find a fix for this windowing bug that would be great by the way. I don't have the expertize to do it unfortunately.

---

