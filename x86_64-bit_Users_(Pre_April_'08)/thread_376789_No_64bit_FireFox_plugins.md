---
title: "No 64bit FireFox plugins?"
date: 2007-03-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by NeilBlanchard on 2007-03-05
Greetings,

In Ubuntu Edgy Eft 6.10 64bit, using FireFox I cannot install the FlashPlayer plugin; because apparently they don't make a 64bit version of the plugin?  Is this the case, or am I missing something?

BTW, the instant email notification in these forums doesn't work for me.  It might be my ISP, but it does work on most other forums, though.

---

### Post by rsambuca on 2007-03-05
If you want flash to work with Firefox, you'll have to install the 32bit version.  You can get the 32bit Firefox installed with the instructions on this [[COLOR="Red"]how-to[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=202537")

---

### Post by blackstealth007 on 2007-03-05
follow these instructions, and you can get it to work [http://www.ubuntuforums.org/showthread.php?t=341727&highlight=nspluginwrapper](http://www.ubuntuforums.org/showthread.php?t=341727&highlight=nspluginwrapper)

---

### Post by Kilz on 2007-03-05
> **blackstealth007 said:**
> follow these instructions, and you can get it to work [http://www.ubuntuforums.org/showthread.php?t=341727&highlight=nspluginwrapper](http://www.ubuntuforums.org/showthread.php?t=341727&highlight=nspluginwrapper)

Nspluginwrapper is good for flash,but it doesnt work with a java plugin. The only java plugin is the old 64bit blackdown that constantly makes the browser crash when opening applets in Firefox 2.0. If the orignal poster also needs java the only way to reliably get it is the 32bit Firefox and plugins.

---

### Post by NeilBlanchard on 2007-03-06
Greetings,

Well, I started down the path of the ns wrapper, but I couldn't get it to work; so, I tried the 32bit version of FireFox -- and things when smoothly, and it is all up an running!  I can run both the 64bit and the 32bit, as needed.  I found that I had to restart both versions in order for the Flash plugin to work.  (I was leaving the 64bit version up, so I could reference the instructions as I went.)

Thank you to all who helped!  :KS

---

### Post by Popoi on 2007-03-06
I have installed Firefox 62-Bit Version, works nice! :D

---

### Post by Moordrik on 2007-03-13
Yep I can second that the instructions for the 32 bit install of FF, flash 9, java works flawlessly for me as well. :)

---

### Post by FredB on 2007-03-14
Well, I was using nspluginwrapper for flash 9 when my herd 5 was fully working.

The only point is not to forget libasound32 in order to have sound in flash enabled pages.

Since there is no gnome-panel package for AMD64, I have to boot on an old Dapper Drake live CD to seek for answers. :(

---

