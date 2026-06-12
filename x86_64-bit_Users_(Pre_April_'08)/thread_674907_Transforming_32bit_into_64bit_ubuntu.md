---
title: "Transforming 32bit into 64bit ubuntu?"
date: 2008-01-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by heatblazer on 2008-01-22
Recently, thanks to 2 users from the forum, I was able to solve a problem connected to the installation of a 64 bit ubuntu on my hardware. Now I have a question - can I transform my current 32bit ubuntu into the 64 bit one, without loosing my system?
 Personally, I don`t think that is possible, but better ask than suspect.

---

### Post by FriedChips on 2008-01-22
Not reasonably easily. I have read of many many problems that attempting that causes. Best to do a clean install.

---

### Post by Thelasko on 2008-01-22
I have made the transition myself.  I recommend doing a clean install.

In theory you can do a clean install and simply use the same \home folder that you used for 32-bit.  I had problems with this method.  Your settings files may not transfer "nicely" from one install to another(settings files are files that start with "." in your /home directory).  For example, if you transfer your .Gnome folder over you will have setting in your applications menu that will not be installed on your system. You can move your files over but I don't recommend moving settings.

If you feel bold you can move your settings over and then if you have problems with a program simply delete the settings folder and the program will create a new one the next time it launches.  I have tried this and have found Firefox's settings to be fairly robust.


Anybody have similar experiences?

---

### Post by heatblazer on 2008-01-23
:S Looks like a quite bold action... Well, I`ll just wait the new distro ver 8.xx and install it clean on my HDD.

---

### Post by Thelasko on 2008-01-23
If you don't care about settings and just want to migrate your data it's not hard at all.  Just save your data to some other media (CD, DVD, another HD or partition) and reinstall Ubuntu.  Once your system is installed just move your data back over.

I would say the steps above take under an hour.  If you have other programs add another hour.  If you have special settings you need to make (like a graphics card) it could take longer.

---

