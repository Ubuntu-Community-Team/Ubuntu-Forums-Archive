---
title: "Problems installing Starcraft"
date: 2008-07-06
forum: Wine
---

### Post by jlapaglia on 2008-07-06
I'm having a problem installing the game Starcraft. I have wine installed and have never had a problem with wine. 

I searched this problem for almost 6 hours days and found a whole lot of nothing.

I run the install.exe through wine and it starts up like it should, the installation window appears with sound and everything, then I enter the key, Next it asks me where I want to install the program (C:/Program Files/Starcraft) which is where the problem is. When i click ok, this error appears

"The specified folder 

C:/Program Files/Starcraft 

is invalid, incomplete, too long or write protected. Enter a full path with a drive letter; for example:

C:/Starcraft"

However, no matter what drive i select or folder i tell it to install in it gives me the same error.

---

### Post by kdorf on 2008-07-06
Windows uses backslashes (\) instead of slashes. It should be C:\Program Files\Starcraft.

That may be your problem.

---

### Post by jlapaglia on 2008-07-06
Nope, I'm just mildly illiterate and accidently posted the wrong slash, they actually are backslashes in the installation.

---

### Post by jlapaglia on 2008-07-07
Upon completely uninstalling wine and removing the hidden .wine folder from my home folder and then reinstalling wine, the installation went flawless

---

### Post by tamoneya on 2008-07-07
im not sure if it interests you but I recently found this nice tutorial that may be convenient: [http://ubuntu-tutorials.com/2008/07/06/install-the-1152-no-cd-patch-for-starcraft-on-ubuntu-804/](http://ubuntu-tutorials.com/2008/07/06/install-the-1152-no-cd-patch-for-starcraft-on-ubuntu-804/)

---

