---
title: "How do i run something in 95 compitability"
date: 2008-03-25
forum: Wine
---

### Post by Funky91 on 2008-03-25
I am trying to install House of the Dead on my computer and I need it to run for Windows 95 compatibility otherwise the setup file says that it cannot find a particular file (it also does this in XP unless I set the compatibility down).

How do I set the compatibility down in WINE? I have tried using wine cfg but when I open the file it comes up with the same error. Is there a particular way I need to open it?

---

### Post by Triggerhapp on 2008-03-25
What file? Wine's Appdb is scarily empty, first time ive seen it empty on any subject XD

---

### Post by Funky91 on 2008-03-25
It is a file it is trying to find on the CD.

Here is a screenshot of the error.

---

### Post by kostkon on 2008-03-25
> **Funky91 said:**
> I am trying to install House of the Dead on my computer and I need it to run for Windows 95 compatibility otherwise the setup file says that it cannot find a particular file (it also does this in XP unless I set the compatibility down).

How do I set the compatibility down in WINE? I have tried using wine cfg but when I open the file it comes up with the same error. Is there a particular way I need to open it?
If you think that's the reason you get this error, then open a terminal and run *winecfg*, i.e. like this
```
winecfg
```
then select the *Applications* tab, and having the *Default Settings* selected, change the *Windows Version* to *Windows 95*. Also, make sure that your CD/DVD drive is recognized as a drive in the *Drives* tab. If it does not exist there, then add it yourself.

---

### Post by Funky91 on 2008-03-25
I have now done all that but it still comes up with the same error. Does that mean that I will not be able to run it?

---

### Post by kostkon on 2008-03-25
Try to use another Windows version in *winecfg*, e.g. W*indows 2000*, etc. Try all the available options, it may work for one of them. Does the file *SETUP.INS* actually exist in the CD?

---

### Post by Funky91 on 2008-03-26
The file is on the CD. It is not in the CD but it is not in the main page. It is in D:/install/ENGLISH.

I have tried all the different windows options with no sucess.

---

### Post by kostkon on 2008-04-01
Hmmmm. I don't know what else to recommend you. 

One solution would be to make an ISO image of the CD (by right clicking on the CD and selecting *Copy Disk*), [mount the ISO to your system]("http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html"), and copy the file in question (*SETUP.INS*) from *D:/install/ENGLISH* to *D:/* (to say it in simple words).

Finally, add the mounted ISO image as a drive in *Wine* (using *winecfg*) and then try again to install the game.

This way you should be able to play the game without the need for the CD.

Before doing the above, you could try copying the file SETUP.INS to the *windows* wine folder.

You will find the *windows* folder in
```
/home/yourusername/.wine/drive_c/windows
```

Open a nautilus window and select *View -> Show Hidden Folders* to easily find this folder using the file browser.

---

