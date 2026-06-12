---
title: "Troubles installing Civilization IV"
date: 2008-05-02
forum: Wine
---

### Post by Aiello on 2008-05-02
I am attempting to install Civ IV through wine and I am having a few problems. First, I run the setup.exe program on the disk and the installer appears to load fine. The installer then prompts me that I need to install DirectX. The DirectX installation window pops up, but it says that an error occurs and the install fails. Both installers (Civ IV and DirectX) then seem to lock up and will not close for quite a long time. 

Any suggestions on how I could possibly install Civ IV successfully?

I am using Wine version 0.9.59 on Ubuntu 7.10.
Sorry for the vague description, but I am relatively new to Linux.

-Thanks!

---

### Post by jacksaff on 2008-05-02
Wine alone is not yet capable of playing CivIV.

The good news though is that you can use some windows code with wine (using native dll overrides) and this allows CivIV to run all-but-perfectly. I have Civ IV complete and the ONLY issue I have is with progress bars not showing on the cities in main view. In other words, it runs better than it did in windows...

You do however need to do a bit of tweaking to get it installed, and have to download a few DirectX9 dlls. You'll also have to find cracked no-cd patched versions of the Civ4 executables.

Go to [http://appdb.winehq.org/objectManager.php?sClass=version&iId=10158](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10158) for detailed instructions.

---

### Post by jayrix on 2008-05-03
Does it works with all the addons for Civ4 ? meaning the expansion packs?

---

### Post by jacksaff on 2008-05-03
Yes, I generally play Beyond the Sword.
You do need to find no-cd cracked .exes for each version you want to play. Wine doesn't have the code to show whether or not a licensed disc is in the drive.
I have an issue with loading mods (normal scenarios have no problems) from within civ where I lose sound. This can be overcome by opening the mod directly with a command line passing the name of the mod to civ4. Can't remember the syntax at the moment, I haven't played a mod for a while.

---

### Post by Aiello on 2008-05-03
Thanks for the info jacksaff, I will have to try that one I get around to it.

---

### Post by Araja on 2009-11-05
I think I have tried everything. I have Wine already installed. Downloaded and configured the dll's. And when I go to play the game I come up to the point where it said to "Play Now" and it sends me back to the computer log in. What do I do? Did I forget something? Do I need to reinstall Civ. 4?

Im running Hardy with Wine version 1.1.32 with Wine Tricks.

---

### Post by pedro_orange on 2009-11-06
Thread back from the dead!!

I would imagine if you've got the game running; you've probably got it setup right. 
What video card do you have? What drivers do you have installed? How did you install them? 

What version of Wine do you have?

---

