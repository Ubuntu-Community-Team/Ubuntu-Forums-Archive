---
title: "wine"
date: 2008-01-22
forum: Wine
---

### Post by vvaffaness on 2008-01-22
how do you open programs with wine?

---

### Post by stoneybroke on 2008-01-22
You need to right click on the .exe file or left click on a desktop icon.

---

### Post by Greg Mueller on 2008-01-22
On some of the apps I've tried to run under Wine, they try to start and then just disappear.

---

### Post by dreadlord_chris on 2008-01-22
> **Greg Mueller said:**
> On some of the apps I've tried to run under Wine, they try to start and then just disappear.

to see what the problems are with these apps - run them from the command line:
```

wine /path/to/app.exe

```

---

### Post by Greg Mueller on 2008-01-22
I tried
wine /home/greg/.wine/drive_c/Program Files/Diffraction Limited/MaxIm DL V4/Maxim_DL.exe

from the terminal and it said
wine: cannot find '/home/greg/.wine/drive_c/Program'

---

### Post by Tadock on 2008-01-22
> **Greg Mueller said:**
> I tried
wine /home/greg/.wine/drive_c/Program Files/Diffraction Limited/MaxIm DL V4/Maxim_DL.exe

from the terminal and it said
wine: cannot find '/home/greg/.wine/drive_c/Program'

the Program Files part needs /Program\ /Files/
Also, you could try just cd /home/greg/.wine/drive_c/Program\ /Files/Diffracation\ /Limited/MaxIm\ /DL\ /V4/
Then wine ./Maxim_DL.exe

---

### Post by Greg Mueller on 2008-01-22
Thanks
 and sorry to Hijack this thread from vvaffaness

---

### Post by Meow27 on 2008-01-22
well i cant tell if this was answered already but ill cut it down short

install the program by right clicking and running with wine

make sure its in the wine program folder ("c drive")

the link should be in ur wine start menu afterwards if not, browse your WIN folder thru the start menu

---

### Post by jacksaff on 2008-01-22
> **Greg Mueller said:**
> I tried
wine /home/greg/.wine/drive_c/Program Files/Diffraction Limited/MaxIm DL V4/Maxim_DL.exe

from the terminal and it said
wine: cannot find '/home/greg/.wine/drive_c/Program'

This is because the shell sees a space as a gap between command arguments and so "Program Files" is seen as two things rather than one. This is why unix always has an underscore "_" instead of a space in filenames. Windows has a different system so you need to escape all those spaces. 
Simpler is to put the whole lot you are passing to wine in double quotes:

wine "/home/greg/.wine/drive_c/Program Files/Diffraction Limited/MaxIm DL V4/Maxim_DL.exe"

You can use that as the command for a shortcut icon as well, or for a menu entry.

---

### Post by Greg Mueller on 2008-01-22
Thank you I'll try that in the morning

---

### Post by Greg Mueller on 2008-01-23
There are two quite similar threads running that I have been posting to. I tried to run these programs from the terminal and have the results posted here

[http://ubuntuforums.org/showthread.php?t=675032](http://ubuntuforums.org/showthread.php?t=675032)

Sorry for the confusion

---

### Post by zeus123 on 2008-12-12
How did you get on with MaximDL on wine??

Im thinking about installing Linux on my ibook so I can use MaximDL or MaxDSLR. Nebulosity is supported on Mac but I own and am used to MaximDL and MaxDSLR.

---

