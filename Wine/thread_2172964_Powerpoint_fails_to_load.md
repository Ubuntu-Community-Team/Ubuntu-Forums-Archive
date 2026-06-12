---
title: "Powerpoint fails to load"
date: 2013-09-07
forum: Wine
---

### Post by jonathan-l-harrison on 2013-09-07
HP Pavilion g6 Laptop
Intel Pentium CPU B960
5.8G Ram
x86_64
13.04 raring
Everything is up to date

Wine, q4wine, PlayonLinux installed

I can not run Powerpoint on my wife's laptop.  It starts, then says it was not opened correctly last time, would I like to open in safe mode.  No matter what I select it flashes the Powerpoint logo and disappears.

I have found nothing in Google searches or in the forum to help.

When i select PlayonLinux I do get this message
[HTML]PlayOnLinux is unable to find the 32bit OpenGL libraries.
You may encounter problems with your games[/HTML]
but I can get in to the app and load the apps from there...  Word and Excel work fine, but not Powerpoint.

i also have a Wine install and installed it in there too, but that has the same error message.

Any ideas, please?  The wife needs Powerpoint for work and is threatening to revert back to Windows after 5 years of Ubuntu....  Please help me.

---

### Post by Toz on 2013-09-07
*Moving to the **Wine** subforum.*

What version of Powerpoint/Office are you using? Did you override riched20 as noted [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=12813") and [here]("http://www.fclose.com/3719/installing-ms-office-2007-on-linux-using-wine/")?

---

### Post by jonathan-l-harrison on 2013-09-07
OK solved it myself in the end.


Needed to change riched20.dll to (native) in winecfg


Either by doing a search (Catfish File Search) for the file "winecfg", opening it and adding riched20 to the list of applications in Library as below, or
by going in to PlayonLinux app, selecting "Configure"
Select the "Virtual Drive" on the left (should be "Office 2007" or so)
Select "Wine" on the right.
"Configure Wine"
Selecting "Libraries" and the selecting it from the drop down menu "New Override for Library".

---

### Post by jonathan-l-harrison on 2013-09-07
Ah, you must have replied as I was typing, Toz
Thank you, but solved..... as you suggested.  Thank you.

---

