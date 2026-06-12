---
title: "[SOLVED] Just getting the thing working"
date: 2007-12-19
forum: Wine
---

### Post by rurinix on 2007-12-19
I have freshly installed Wine via apt-get.  I have searched forums galore for anything which talked about the problem I am having.  I have yet to have found anyone else with this same issue.  I cannot read anything in Wine, it shows up as gibberish.  Not even like a different language, but rather lines, dots and symbols.  The version is 9.46, since that's what came with Gutsy.  I am running on an AMD Athlon XP 2000 with 1GB RAM and over 100GB of free hard drive space (though I doubt any of those would have caused a problem like this).  Based on a suggestions I found form a Wine bug report, I tried to remove TrueType font Tamil, but I couldn't find it installed on my system.  Almost everything installed on this system is stock.  I want to use Wine so that I can use software specific to Windows for test studying.  I know there is no Linux equivalent for this software.  I have attached screenshots of the Wine Config app and Notepad.  As you can see, I can't read anything, but it does read what I type.

Any suggestions?

---

### Post by solar george on 2007-12-19
Try deleting your ~/.wine directory.

---

### Post by rurinix on 2007-12-19
Just for curiosity, I upgraded to 9.51 using a .deb found at the following URL:

[http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/)

Works like a champ now.  Strange...

---

### Post by cogadh on 2007-12-20
That's the official Wine Debian/Ubuntu repository. If you follow the instructions [here](http://winehq.org/site/download-deb), you can set up Ubuntu to use that repository and you will always be kept up to date with the latest Wine through Ubuntu's automatic updates.

---

### Post by rurinix on 2008-01-17
OMG that worked!  Thanks a ton!

---

