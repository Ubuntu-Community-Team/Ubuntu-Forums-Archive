---
title: "Where Does WIne Appear After Installation"
date: 2008-08-13
forum: Wine
---

### Post by arnold.pietersen on 2008-08-13
I downloaded the .deb package for wine_1.0.0 and installed it.  However, I do not see it in Applications > Office

I still have the programs I installed under a previous version of Wine which is located at Wine > Programs.

Any help out there?

---

### Post by flytripper on 2008-08-13
its an entry in the applications menu

---

### Post by arnold.pietersen on 2008-08-13
On which sub menu of the Applications menu does it appear?  As I have indicated I do have the Wine sub menu on the Applications.  Only the programs I have installed under Wine appears there under the programs sub menu.  

I want to run Wine to install other programs and can't find it.

---

### Post by maxmanapple on 2008-08-13
It seems you're trying to find an executable file of Wine. Such thing, however, it doesn't exist. Wine is always running, all you need to do to activate it is running an exe file. Because Wine Is Not an Emulator that must be opened. Wine is a compability layer running alongside Linux.

---

### Post by jacksaff on 2008-08-14
> **maxmanapple said:**
> It seems you're trying to find an executable file of Wine. Such thing, however, it doesn't exist. Wine is always running, all you need to do to activate it is running an exe file. Because Wine Is Not an Emulator that must be opened. Wine is a compability layer running alongside Linux.

Not really. Wine has an executable and it installs to /usr/bin. Have a look, it'll be there. 
Wine doesn't run till you ask it to, and it requires you to give it an argument - something else for it to do it's thing with (ie. a windows binary).
So once wine is installed, you'd run something by typing 
wine /path/to/application.exe
and wine will be started and itself then run "application.exe".
As both gnome and kde allow you to associate a file type with a certain application all of this can happen in the background. You click your .exe and gnome or kde knows that this sort of file should be run by wine and so generates the appropriate command without you needing to type it.

---

### Post by RealG187 on 2008-08-15
right click and pick run with wine.

or use terminal

wine /home/you/Desktop/exanple.exe

you can type "wine " (with space) and drag and drop exe there and it will put the path for you

---

