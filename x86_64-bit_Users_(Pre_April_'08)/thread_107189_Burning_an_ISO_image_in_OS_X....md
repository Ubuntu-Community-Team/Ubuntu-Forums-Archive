---
title: "Burning an ISO image in OS X..."
date: 2005-12-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by ctt1wbw on 2005-12-22
Okay, the wiki did nothing for me, neither did a search in the forums.  How do I burn the iso image of the live cd?  I thought I had it correct, but my mac wouldn't boot off the cd when I was done.

---

### Post by Jason_25 on 2005-12-22
The OSX disk utility works perfect for burning isos.

---

### Post by ctt1wbw on 2005-12-22
Well, I just tried the live cd that I downloaded and nothing happened.  I got to the brown screen, the mouse cursor appeared and that was it.  I'm not too sure if it's the driver for my video card in my iMac or not.

Oh well.

---

### Post by linear on 2005-12-22
Since you said the magic word "iMac" (though not which model) - have you checked for problems in xorg.conf? If this is a model with ATI Rage 128 video, check for incorrect horizontal sync and vertical refresh, and also try disabling dri. Since I don't know how expert you are, instructions below:

After booting is complete,
1. ctrl-option-F1 (should give you a command prompt)
2. type: sudo nano /etc/X11/xorg.conf (return)
3. make your edits (see below)
4. ctrl-O (return) to write edited file
5. ctrl-X to exit nano back to command line
6. type: sudo /etc/init.d/gdm restart (return) to restart Gnome

At the very least you'll need to modify "HorizSync" to 60-60 and "VertRefresh" to 75-117. Both are in the monitors section.

If you restart Gnome and everything is in extreme slo-mo, you'll also need to edit xorg.conf to disable DRI (in the modules section, put a hash mark (#) at the beginning of the line containing "load dri").

---

### Post by ctt1wbw on 2005-12-23
Well, it's a G5 iMac with an ATI video card.  And I didn't get to do anything like what you said above.  It froze on the brown screen with the mouse cursor.  I couldn't even move the cursor at all.

---

### Post by ctt1wbw on 2005-12-23
Well, darnit!  I tried the Dapper Drake live cd and the same thing happened.  I don't know what's going on.  I am not sure I even want to put Ubuntu on my iMac or not...  I might just give the wife the iMac and take my Dell Inspiron 8600 laptop back so I can use Ubuntu...:confused:

---

### Post by kalin on 2005-12-23
Check if the date is set correctly, I've seen an iMac behave exactly like that when the date was reset (it was simply an old machine, probably with an exhausted internal battery).

If you can't boot in OSX to do that you can try doing it command line:
. boot the live CD
. press ctrl+F1 to go to the command line
. type "man date" to see what the options are for the "date" command
. set the correct date (e.g. "date 122317412005" stands for: December 23th 17:14 year 2005)

Hope that helps.

Edit: some more info -
. simply typing "date" will show the current date/time
. you need to reboot after resetting the date in order things to start working

---

### Post by linear on 2005-12-23
Even if you can't move the mouse, try ctrl-option-F1 and see if you can get a command prompt. (Try it a couple of times, and wait several seconds before assuming it didn't work.)

---

### Post by ctt1wbw on 2005-12-25
Well, I downloaded the 5.10 live cd for i386 and put it on my Dell laptop.  I'm loving it.:D

---

### Post by octavedoctor on 2005-12-25
[QUOTE=Jason_25]The OSX disk utility works perfect for burning isos.[/QUOTE]
No it doesn't, I tried it. 

You need Firestarter

[http://www.projectomega.org/subcat.php?lg=en&php=products_firestarter](http://www.projectomega.org/subcat.php?lg=en&php=products_firestarter)

---

### Post by ctt1wbw on 2005-12-25
I've just used the OS X Disk Utility.  It works perfectly.

---

### Post by ctt1wbw on 2005-12-26
Okay, someone help me out here.  I've tried the live cd copy of Breezy Badger and Dapper Drake on my G5 iMac.  Both times I managed to get through the screen resolution choice, detecting hardware, etc etc etc.  The next step I see is Ubuntu going through the checklist  and detecting things and saying ...ok next to each item.  A second or two after that, the screen goes brown and I see the cursor.  I can move the cursor about one or two seconds, then the system hangs.  I let it sit like that for about 10 minutes hoping something would happen but it didn't.  I could not type any key combinations to get to the terminal.  Nothing happens.

By the way, my iMac has the ATI Radeon 9600 chip in it...

I would love some help here because if I can figure this out, I might erase OS X and go 100% Ubuntu.  :D

---

### Post by linear on 2005-12-26
Well, here is a new suggestion just posted in the Dapper Drake forum:

[http://ubuntuforums.org/showthread.php?t=108600](http://ubuntuforums.org/showthread.php?t=108600)

Fixes KDE for the iMac G5, suggests it might work for Gnome, but I don't quite follow how you can rename a file if you can't get to the gui or a command prompt...

---

### Post by ctt1wbw on 2005-12-27
Me neither.  I'm downloading the Kubuntu live cd now.  I'll try it when I can get around to it.  Hopefully I can use that.  :???:

---

### Post by jdp on 2005-12-31
[QUOTE=octavedoctor]No it doesn't, I tried it. 

You need Firestarter

[http://www.projectomega.org/subcat.php?lg=en&php=products_firestarter](http://www.projectomega.org/subcat.php?lg=en&php=products_firestarter)[/QUOTE]

Are you using a stock/known compatible drive or a 3rd party aftermarket drive?  If the burner shows up to burn in iTunes, then Disc Utility should be able to burn .iso files on it too.

---

