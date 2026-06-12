---
title: "Microsoft Office 2003 Problems in Wine"
date: 2007-11-27
forum: Wine
---

### Post by Udders3 on 2007-11-27
.

---

### Post by cogadh on 2007-11-27
You should check Wine's Application Database for application specifics when using Wine. The entry for Office 2003 has this advice:

[I]"Simply install with Wine 0.9.46. When you launch any program, it will say that the program isn't installed for the current user. Don't panic. Remove Wine ("sudo aptitude remove wine" for me). Install Wine 0.9.37. Launch any program. It will work. Now update your Wine version to 0.9.46, relaunch the programs, and.... Magic! It works. Simply PowerPoint is slow, and I've not tested Excel very much, but it seems to work!!"
[/I][http://appdb.winehq.org/objectManager.php?sClass=version&iId=3214](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3214)

It should be noted that the Access, OneNote, Frontpage, Infopath and Outlook applications in Office 2003 do not work with Wine at all.

---

### Post by Udders3 on 2007-11-28
.

---

### Post by mthakur2006 on 2007-12-16
u manage allright then?

---

### Post by lee140685 on 2007-12-22
i have try what you suggest but it not works at all the result still the same :confused:

---

### Post by mvcisback on 2008-01-29
I currently have onenote running on Ubuntu. the sound, video, and templates are not functioning. However notetaking functions as well as in windows. Currently you must create new sections by copying it within the "My Notebook" folder. 
(major glitch workaround is copying the msls.dll from a windows computer with Onenote installed into your wine system 32)

p.s.Further help appreciated

---

### Post by Whiffle on 2008-01-29
I got it to install yesterday with the latest version of wine available from the winehq repository.  It game me that error mentioned above about users.  The Solution is to re-run the setup program and click the Repair option.  Other than that it works quite well.

---

### Post by mvcisback on 2008-01-29
Is your onenote opening sections within itself? or audio? im currently able to take limited notes but thats all i need.

---

### Post by Whiffle on 2008-01-29
I don't have onenote.

---

