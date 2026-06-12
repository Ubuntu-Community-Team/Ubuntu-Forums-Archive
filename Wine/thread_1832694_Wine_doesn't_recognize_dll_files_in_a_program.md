---
title: "Wine doesn't recognize dll files in a program"
date: 2011-08-25
forum: Wine
---

### Post by BlackoutWorm on 2011-08-25
Hey. I checked winehq, and there it says my program will work just fine in wine.
But it asks for a bunch of DLL files even though they are in the folder.
Is there a way to fix this?
The exact same version of the program was listed as PLATINUM on winehq, so this is strange.

---

### Post by ilantal on 2011-08-25
Rather than Wine, I prefer VirtualBox. It is much more powerful. I've got to support some old Microsoft crap, so I run Windows XP as a guest of Ubuntu. Inside the Virtual box I can run Visual Studio, and even games if I want to do so.

---

### Post by BlackoutWorm on 2011-08-25
thanx but the graphic is horrible, and it's in a window.
Anyway, that's out of the question.
So can somebody help me with this please?

---

### Post by colin.p on 2011-08-25
I use both wine, as well as XP in a VB, for the couple win programs I still use. However, I do have a problem with one particular program, whenever there is an update. I then go to wineHQ and very shortly, someone posts a fix. That may be your best bet. You can be fairly sure someone has had the same issues and will post a fix.

edit: you can also post your question at wineHQ

---

### Post by philinux on 2011-08-25
Moved to Wine forum.

---

### Post by cottfcfan on 2011-08-25
What Wine version are you using & what program are you trying to install?

---

### Post by BlackoutWorm on 2011-08-25
The newest wine version. I Use the wine-ubuntu ppa from their website. And the program I try to install is Magix Music Maker 17 premium.
When I try to open the program it tells me that some dll files are missing even though they are there.

---

### Post by cottfcfan on 2011-08-25
the Problem may be the Wine version you are using.
Wine 1.3xx is really a beta version. wine 1.2xx is the stable version.
See which one you installed and try the other one.

---

### Post by BlackoutWorm on 2011-08-25
I installed the 1.2 version.
wine-ubuntu is the stable ppa.
So, what you are saying is that DLL is not supported in older versions?

---

### Post by cottfcfan on 2011-08-25
I don't know what the problem is, but I do know that more programs seem to work with a later version of Wine.
Try uninstalling 1.2.3, and install 1.3.26 instead. you may find it works.

---

### Post by BlackoutWorm on 2011-08-26
Problem solved:) (Sort of)
I googled some more and learned that more people have the same problem with DLL files not being recognized.
And someone said if I either install the program through playonlinux or run the program or game from there, it should work fine. He basically use this command to run the program:
/usr/share/playonlinux/playonlinux --run "/path/to/.exe"
For some reason, PlayOnLinux does recognize the DLL files.
I imagine that a lot of the apps on winehq that people have tested and marked as "garbage" will actually work if they do it this way.

And again, thanks for all your help and support, guys!

---

