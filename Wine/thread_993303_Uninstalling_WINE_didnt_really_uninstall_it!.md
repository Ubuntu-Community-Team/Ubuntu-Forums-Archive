---
title: "Uninstalling WINE didnt really uninstall it!"
date: 2008-11-25
forum: Wine
---

### Post by iheartubuntu on 2008-11-25
Ive been have a couple of problems with some software in Wine, so I decided to back up the Wine directory and then uninstall Wine. I used Synaptic and did a complete removal of Wine. Well, after rebooting, the .wine folder was still there (not the backup one) and the wine menu items were still in place.

Can anyone clue me in why uninstalling wine didnt work for me? Id like to reinstall a fresh Wine DEB and reinstall all my Wine related software.

---

### Post by hikaricore on 2008-11-25
To completely uninstall wine you must right-click on the package in Synaptic and chose:

Mark For **Complete** Removal

Simply removing the .wine directory will remove your user files which are the only thing left after a standard removal.

Hope this makes sense.  :)

---

### Post by cogadh on 2008-11-25
Also, you will need to manually delete the menu shortcuts for any programs you have installed with Wine. They always get left behind after an uninstall.

---

### Post by iheartubuntu on 2008-11-25
> **hikaricore said:**
> To completely uninstall wine you must right-click on the package in Synaptic and chose:

Mark For **Complete** Removal

Simply removing the .wine directory will remove your user files which are the only thing left after a standard removal.

Hope this makes sense.  :)

I did do a COMPLETE removal of Wine. I also deleted the .wine folder. After rebooting, I installed Wine from a new 1.1.9 DEB file, rebooted again and went to my home directory and there it was... the .wine folder as it was before I started any of this. All of my programs still there as if I had never deleted Wine in the first place. ???? :confused:

---

### Post by cogadh on 2008-11-25
When you made the backup, did you just make a copy the existing .wine directory? If so, that's why it was still there. Uninstalling Wine does not remove the .wine directory, you need to delete it manually yourself.

---

### Post by iheartubuntu on 2008-11-25
> **cogadh said:**
> When you made the backup, did you just make a copy the existing .wine directory? If so, that's why it was still there. Uninstalling Wine does not remove the .wine directory, you need to delete it manually yourself.

I copied the .wine directory to another folder on my HD, and also renamed the .wine folder backup to "DOG" and to avoid any confusion. I did notice however that even though I named the folder DOG, it was still invisible.

---

### Post by iheartubuntu on 2008-11-25
What would be the correct way to uninstall WINE, and reinstall it from a clean slate. Here is how I did it...

-backup .wine folder to another directory and rename .wine folder to something else.

-uninstall Wine through Synaptic and select for complete removal.

-delete original .wine folder

-reboot

-install Wine from new DEB file

NOW WHAT? This is where I am stuck. After installing Wine from the DEB, my .wine folder was completely restored with all of the programs still there!

---

### Post by cogadh on 2008-11-25
I really don't see how that is possible, since just installing Wine doesn't even create the .wine directory, that doesn't happen until you launch Wine or run winecfg for the first time. 

However, all you really need to do is just delete the .wine directory you have right now, then create a brand new one by running winecfg.

---

### Post by iheartubuntu on 2008-11-25
OK, here goes.... Trying it all over again :popcorn:

I just copied the .wine folder to someplace else. I now have the original .wine directory and another .wine directory in another folder elsewhere.

I rebooted and got the error...
> 
users $home/.dmrc file is being ignored

I fixed that problem by going here and using the tip from post #8: [http://ubuntuforums.org/showthread.php?t=371052](http://ubuntuforums.org/showthread.php?t=371052)

Using Synaptic, I uninstall Wine by right clicking and marking it for "Complete Removal". I then click "Apply" to remove Wine. I check my Applications menu and while Wine is still listed with the programs menu, there is no longer any Wine config or other Wine options normally in the Wine menu folder. I also make note the original .wine folder is still there. Am now deleting the original .wine folder and emptying my trash. Will reboot and come back.

---

### Post by iheartubuntu on 2008-11-25
OK, Ive rebooted. No .wine folder still. I will now attempt to install the most recent stable version of Wine which is 1.0.1. Usually I always install the most recent version (like 1.1.9). I dont see 1.0.1 available so I choose 1.0.0 instead. Picking the appropriate DEB for my machine (i386).

After installation, I check the Wine folder in Applications. I now see the config option. I check my home directory and .wine is not there yet. I now click "Configure Wine", click all the tabs. Click OK to exit the config.

There is now an EMPTY .wine directory.

[SIZE="5"]YAY!!! Thank you![/SIZE]

We'll see what happens now :) I'll try to install some software.

---

### Post by iheartubuntu on 2008-11-25
OK, while it appears to be a  totally fresh install.... someplace the computer retains all my info for programs.

If I go here:

/home/dave/.wine/drive_c/windows/profiles/dave/My Documents

Then all my old info is still there.

---

### Post by cogadh on 2008-11-25
That "My Documents" directory is not an actual directory, its just a symlink that points to your home directory (/home/dave). It is automatically created with the .wine directory.

EDIT - Just to clarify a little, if you see anything in that "My Documents" directory, its not because Wine is saving settings somewhere, its because those items are actually still in your home directory.

---

