---
title: "Wine, how do I enter C drive!?"
date: 2013-11-09
forum: Wine
---

### Post by Niemil on 2013-11-09
Well, I trying to install Photoshop CC on Ubuntu 12.10 and I'm very newbie into this. I used Ubuntu before but I gave up on it. Decided not to give up now though, I really want/need photoshop CC installed on the computer.
I am following this guide
[http://www.makeuseof.com/tag/idiots-guide-installing-photoshop-cs5-ubuntu-1004/](http://www.makeuseof.com/tag/idiots-guide-installing-photoshop-cs5-ubuntu-1004/)

What's not told is how I access the C drive.
They say "go applications then wine".
First of all, how do I even go to applications?

Second, I don't even have anything named Wine. I have "Configure wine" and "Winetricks", and none of them seem to give me access to the C drive.

Googled and saw some thread where they said it can be access via host folder, but cannot even find that one.
Some other dude said it's in home/.wine/
But I don't even have any .wine folder.

---

### Post by cmcanulty on 2013-11-09
In your home folder under view make sure show hidden files is checked. Then in .wine folder you will find c drive

---

### Post by Frogs Hair on 2013-11-09
The guide is for a no longer supported of Ubuntu version and may not apply unless you are using 10.04 . Access to the virtual C is via Wine according to the instructions. Have you installed Wine ?  If not it is in the software-center and the instruction specifies getting familiar with it  .

---

### Post by Niemil on 2013-11-10
Ok thanks. I found out that it's CTRL+H or something like that to unhide the folders.


Well, I didn't get the install to complete. Not working for CC, CS6 and now will try on CS5, if not that work I will just google around more.

---

### Post by Mark Phelps on 2013-11-10
First of all, Wine does not mount your existing Windows "C:" drive; instead, it uses the Ubuntu file system and creates files and folders inside that.  It's not an emulation of MS Windows, so it's not running any kind of virtual machine.  And, it does not run apps from your existing MS Windows install; instead, it runs apps you install using Wine.

Also, BEFORE you charge into using Wine a lot, you could save yourself a lot of grief if you go to the WineHQ website and look up the ratings for the apps you want to run:  [http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

Anything not listed, or rated lower than Gold is essentially a waste of your time.

---

### Post by oldos2er on 2013-11-10
Moved to Wine.

---

### Post by yCAxYRA on 2013-11-19
alternative solution would be to use wine file manager by writing winefile to console.

---

