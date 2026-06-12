---
title: "MS Reader with Wine for 8.04"
date: 2008-05-09
forum: Wine
---

### Post by muhd on 2008-05-09
I have tried doing this, following various how-tos and whatnot, but nothing seems to work for me.  Every way I try it, when I start up MS Reader it just gives me what I think is the splash screen which says it isn't activated and then closes.

Please help, I would love to use this program...

Thanks!

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=1003&iTestingId=13053]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=1003&iTestingId=13053")

---

### Post by moresun on 2008-05-11
I have the same problem.
The Reader starts and closes after it showed me the first screen.

I am also looking for help

---

### Post by muhd on 2008-05-12
IIRC, this problem occurred whether I had installed IE6 (which MS reader is supposedly dependent on) or not.  So my initial thoughts are that for whatever reason, MS Reader is not able to get what it needs from internet explorer, which I installed with ies4linux.

---

### Post by muhd on 2008-05-18
So I figured out how to fix the closing problem...

All you need to do is download msvcirt.dll and put it in the windows/system directory.  YAY!

---

### Post by saratchandra on 2008-05-19
> **muhd said:**
> So I figured out how to fix the closing problem...

All you need to do is download msvcirt.dll and put it in the windows/system directory.  YAY!

You can also copy it from the windows/system32 folder of your windoes partition:)

---

### Post by Rayaz on 2008-05-19
It works! I had been looking for the past one day to be able to read my .lit files with no success. Thank you very much:)

---

### Post by Rayaz on 2008-05-19
But how do I open my .lit files with it?:(

---

### Post by Rayaz on 2008-05-19
Got it. Copy the .lit files you have in your "My Library" folder in /home/username/.wine/drive_C/windows/profiles/username/My Documents/My Library and you're off!
Thanks all. :)

---

