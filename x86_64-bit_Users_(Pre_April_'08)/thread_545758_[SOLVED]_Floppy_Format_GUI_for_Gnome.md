---
title: "[SOLVED] Floppy Format GUI for Gnome?"
date: 2007-09-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by crjackson on 2007-09-08
Okay, so I've searched ubuntu but didn't find a good solution.  One thread says 

applications>system>floppy formatter but that doesn't exist on my system.

I also did a google search and it clearly shows that right clicking on the mounted disk icon brings up a formatting dialog.  Mine doesn't.

I installed kfloppy, but I'd rather have a gnome app like the one I saw in google.

Someone please give me the skinny on this.  I'm clearly not finding it on my own.

Thank in advance...

---

### Post by crjackson on 2007-09-08
.

---

### Post by srt4play on 2007-09-08
Check this thread, there is a link to a gnome-utils deb which includes gfloppy.

[http://ubuntuforums.org/showthread.php?t=456210&highlight=gfloppy](http://ubuntuforums.org/showthread.php?t=456210&highlight=gfloppy)

---

### Post by crjackson on 2007-09-08
> **srt4play said:**
> Check this thread, there is a link to a gnome-utils deb which includes gfloppy.

[http://ubuntuforums.org/showthread.php?t=456210&highlight=gfloppy](http://ubuntuforums.org/showthread.php?t=456210&highlight=gfloppy)

I read the thread and checked out the deb.  It's a 32 bit deb.  I'm not sure it would be a good idea to replace my 64 bit desktop utils with 32 bit code.

I'm sure there must be some way to enable this I just don't know how.

---

### Post by srt4play on 2007-09-08
Sorry, there's no way to enable it because it was purposefully left out of the utils package.  You're going to have to find a 64-bit deb that includes it or compile from source.

---

### Post by crjackson on 2007-09-08
> **srt4play said:**
> Sorry, there's no way to enable it because it was purposefully left out of the utils package.  You're going to have to find a 64-bit deb that includes it or compile from source.

A google search finds nothing.  Where would I find the source?  And why would they disable a still useful function.  I still use boot floppies for BIOS flashing.

---

### Post by srt4play on 2007-09-08
The command line utility fdformat is still available so you could use that.  The source is [here]("http://ftp.gnome.org/pub/gnome/sources/gfloppy/") but I have no idea if it can be compiled for a 64-bit system.

---

### Post by crjackson on 2007-09-08
> **srt4play said:**
> The command line utility fdformat is still available so you could use that.  The source is [here]("http://ftp.gnome.org/pub/gnome/sources/gfloppy/") but I have no idea if it can be compiled for a 64-bit system.

Thanks - I downloaded the file and tried to compile.  Unfortunituly I don't know what I'm doing when it comes to compiling.  I know ./configure     make       make install

If that doesn't work then I'm always lost.  Such was the case once again I'm afraid.  In fact, the ONLY thing that has ever complied for me was the ndiswrapper.

I simply don't know what I'm doing.  That's why I look for tools like these...

---

### Post by Yellow Pasque on 2007-09-08
I tried compiling the gfloppy code on 64-bit Gutsy. Unfortunately, I couldn't get it to build because of errors in the GLADE header files. :(

---

### Post by Yellow Pasque on 2007-09-08
I should have done the obvious first. I just went to the terminal and typed 'gfloppy' and sure enough, it's installed on my system (Gutsy Tribe 5,  gnome-utils 2.19.92-0ubuntu). I don't have a floppy drive on my system, so I couldn't get to the main window and test it for you (sorry).

Anyway, the program is part of the gnome-utils package. I read the other thread that srt4play linked and it appears gfloppy is disabled for some reason in Feisty. You might try uninstalling gnome-utils in synaptic package manager and then install the version from this page: [http://linuxappfinder.com/package/gnome-utils](http://linuxappfinder.com/package/gnome-utils)
Hopefully, gfloppy is enabled by default on that one. Good luck.

---

### Post by crjackson on 2007-09-08
> **Temüjin said:**
> I should have done the obvious first. I just went to the terminal and typed 'gfloppy' and sure enough, it's installed on my system (Gutsy Tribe 5,  gnome-utils 2.19.92-0ubuntu). I don't have a floppy drive on my system, so I couldn't get to the main window and test it for you (sorry).

Anyway, the program is part of the gnome-utils package. I read the other thread that srt4play linked and it appears gfloppy is disabled for some reason in Feisty. You might try uninstalling gnome-utils in synaptic package manager and then install the version from this page: [http://linuxappfinder.com/package/gnome-utils](http://linuxappfinder.com/package/gnome-utils)
Hopefully, gfloppy is enabled by default on that one. Good luck.

Thanks for the suggestion but it didn't work.  The build listed for gutsy isn't a working link.  I reinstalled the deb for feisty but it didn't change anything.  It just reinstalled the exact same version.

Thanks for trying though...  Perhaps it will be working on the final gutsy.

---

### Post by sawjew on 2007-09-10
You might want to check out this [http://ubuntuforums.org/showthread.php?p=1778405#post1778405]("http://ubuntuforums.org/showthread.php?p=1778405#post1778405").

I use this script in 64 bit feisty for formatting flash drives and it should work for floppies as well.  I can't test it as I don't have a floppy drive.

I have this in the nautilus scripts folder and I can just right click, go to >scripts>format and format graphically in any of a number of different formats and I can even name them at the same time.

Works great thanks to Bodhi.

---

### Post by crjackson on 2007-09-10
> **sawjew said:**
> You might want to check out this [http://ubuntuforums.org/showthread.php?p=1778405#post1778405]("http://ubuntuforums.org/showthread.php?p=1778405#post1778405").

I use this script in 64 bit feisty for formatting flash drives and it should work for floppies as well.  I can't test it as I don't have a floppy drive.

I have this in the nautilus scripts folder and I can just right click, go to >scripts>format and format graphically in any of a number of different formats and I can even name them at the same time.

Works great thanks to Bodhi.

Actually I'm looking for a GUI application.  I wanted Gfloppy since it intergrates into the Gnome DTE/Nautilus.  I have the source code and I'll hang on to it.  Maybe some day I'll learn how to comple the thing.  For now, I guess the KDE GUI application will work - Kfloppy.

**I wonder if there is a way to create a DOS BOOT floppy under linux.  One that could be used for doing BIOS upgrades.**

---

### Post by sawjew on 2007-09-10
> Actually I'm looking for a GUI application

The script I referred you to actually is a gui using zenity.  You just right click and then go through the steps in the graphical interface.

---

### Post by crjackson on 2007-09-10
> **sawjew said:**
> The script I referred you to actually is a gui using zenity.  You just right click and then go through the steps in the graphical interface.

Cool, I'll have a look at it...

---

### Post by crjackson on 2007-10-19
Installed Gutsy and all is good now...

---

