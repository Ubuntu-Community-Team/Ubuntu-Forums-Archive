---
title: "Repairing a short cut's appearance."
date: 2008-05-22
forum: Wine
---

### Post by gwm on 2008-05-22
Hi,
I installed a windose program. The install placed a short cut on my desktop very nicely.

However, on my wife's machine, the icon is blank. Reinstalling gives the same result, so I thought to copy the icon from a screen shot on my PC and port it to her PC where I could install it manually. (I have Hardy Heron and the latest wine from WineHQ)

Another thread told me how to do the last part and explained that I need an image in  svg format - whatever that is.

Wouldn't it be easier if I could somehow retrieve the icon that resides in the installed exe file? How do I get at it?

---

### Post by SidStudios on 2008-05-22
> **gwm said:**
> Hi,
Wouldn't it be easier if I could somehow retrieve the icon that resides in the installed exe file? How do I get at it?

Yeah. You can use ResHacker, (Resource Hacker) and open up the EXE file in it. Then, in one of the menus, it will let you "Save" the icon file.

---

### Post by gwm on 2008-05-23
Thanx Sid,
I didn't find ResHacker in the repositories, so I guess you're speaking of hacking it from the windows file in windows. I'll google it.

---

### Post by Victor516 on 2008-05-23
There is a program called wineicons that I use to get icons from windows programs. The web site for the program is [http://wineicons.sourceforge.net/](http://wineicons.sourceforge.net/)
When you download you don't need to install it just extract and run wineicons.exe with wine.

---

### Post by gwm on 2008-06-12
Thanks Victor,
I've downloaded it and put it in my store of goodies.
While wandering around the wine directory tree, I stumbled upon a temp folder that contained the missing icon as an image file (.mga I think it was) so I manually added it to the shortcut (sorry - launcher) as others in these threads suggested and there it was!
I have no idea how it got there or why it didn't install correctly on that PC. It worked fine on mine.
:lolflag:

---

