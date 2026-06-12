---
title: "Launching Windows Apps with Wine"
date: 2011-08-14
forum: Wine
---

### Post by wilco0629 on 2011-08-14
I installed Corel Painter in Windows and I would like to run it in Ubuntu. However the program somehow does not allow me to access the executable file. I right click the file and select properties, then I select the Permissions tab and where it says "Execute" there is a check box that states " Allow executing file as program". But when I check it, it is automatically cleared. How do I go about overriding this clearance? I would also like to intall Adobe software, but I imagine I will encounter the same problem.
Thanks in advance for any help.

~Wilco0629

---

### Post by Elfy on 2011-08-14
Thread moved to Wine.

[Looking at the wine appdb - corel painter manages a rating of garbage. ]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=9119")

To set the executable flag in the command line

sudo chmod +x /path/to/file

---

### Post by 3rdalbum on 2011-08-14
> **wilco0629 said:**
> I installed Corel Painter in Windows and I would like to run it in Ubuntu. However the program somehow does not allow me to access the executable file. I right click the file and select properties, then I select the Permissions tab and where it says "Execute" there is a check box that states " Allow executing file as program". But when I check it, it is automatically cleared.

Well firstly, you need to install the program within Wine. You can't usually run programs straight from the Windows system.

Secondly, you can't set an execute permission on a filesystem that is read-only (such as a CD) or that doesn't support the execute permission flag (such as any Windows filesystems).

To get around this, you can open up a terminal, type *wine*, press the space bar to leave a space at the end, and then drag the program to the terminal window. This basically creates the command needed to run Wine with the program you want. Pressing Enter in the terminal window will run the command.

---

### Post by wilco0629 on 2011-08-14
In response to 3rdalbums reply: Dragging the file to the command prompt allowed the file to execute, however, the program stalled with a blank setup dialog box. Perhaps the software does not want to cooperate. Trying to execute the installed .exe application also failed as you said would be the case. Any other ideas or is this just a no win situation as forestpiskie suggests?

---

### Post by Mark Phelps on 2011-08-14
You were already told the app had a rating of "garbage" in the WineHQ database.  That means it will NOT work -- no matter what you do.

---

