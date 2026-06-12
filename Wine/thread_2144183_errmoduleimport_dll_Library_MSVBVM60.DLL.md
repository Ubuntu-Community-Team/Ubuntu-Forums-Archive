---
title: "err:module:import_dll Library MSVBVM60.DLL???"
date: 2013-05-11
forum: Wine
---

### Post by PDA1 on 2013-05-11
I just recently installed wine-1.5.29

Winetricks has been installed

I'm running Ubuntu 12.04 with Gnome desktop

I get the following error message when trying to run Wine (via the right-click on the program I want to run name):

err:module:import_dll Library MSVBVM60.DLL (which is needed by L"Z: \\home\\Formula1\\Desktop\\CelNav.exe") not found


Would you please tell me exactly how to fix this problem?

---

### Post by ranger1021994 on 2013-05-11
Install Microsoft Visual Basic again using WINE

---

### Post by PDA1 on 2013-05-11
Exactly how do I do that?

---

### Post by Mark Phelps on 2013-05-11
Sorry to say it, but you're most likely NOT going to be able to get the Celestial Navigation program to work in Wine.  There's no record of it in the WineHQ database, and without that, there are no hints to be had on getting it installed or working.

You're welcome to read through the WineHQ page on VB (linked below) ... but it's not encouraging:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=94]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=94")

---

### Post by PDA1 on 2013-05-11
It's a little late- I got the Cel Nav program to work nicely.


Somehow I figured a way to install that DLL file and all is well.

---

### Post by Lightning Dragon on 2013-05-11
Hi,

Would you mind sharing your findings with the community in case someone else wishes to run the program? Or perhaps post how you did it on the wine database site?

---

### Post by PDA1 on 2013-05-11
This is how I THINK I did it-

Command line.....

Installed winetricks (somehow)

$ winetricks

Then "Select the default wine prefix"

OK

Then "Install a Windows DLL or component"


Then the computer does some mumbo jumbo and the command line tells you where to install the soon to be installed file.


Once does all worked well.

---

