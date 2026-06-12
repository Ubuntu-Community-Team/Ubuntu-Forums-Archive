---
title: "Help, newbie cant get ubuntu to even start, need to install graphics drivers!"
date: 2005-11-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by p8ntballa06 on 2005-11-07
Hello, i have an ATI X600 graphics card, and im trying to install ubuntu onto my desktop. When i go to start xwindow gives me an error, and i have read around and found out that i need a new driver installed, but the problem is that i cant figure out how to install it.

i have ATI's latest linux driver "ati-driver-8.18.8-x86_64.run"

How do i install this being logged in as root? i cant even get into the GUI to insall it.

Thanks,
Brad

---

### Post by RAOF on 2005-11-07
Here's a complete [howto]("http://ubuntuforums.org/showthread.php?p=423589").  All of that should be able to be done from the console.

---

### Post by p8ntballa06 on 2005-11-07
alright, i tried that, when i do the first step, i get "E: Couldnt find package module-assistant"

and i went on to get this from the ATI installer:

"./packages/Ubuntu/ati-packager.sh: line 49: dpkg-architecture: command not found" and "cp: cannot stat '/ati/fglrx-install/x680/*': No such File or directory"

then i get a "Package build failed"

---

### Post by RAOF on 2005-11-08
Have you enabled the universe/multiverse repositories?  Try [here]("http://help.ubuntu.com/starterguide/C/ch02.html") for help installing stuff.

As a tempory measure, you should be able to get to a GUI by running "sudo dpkg-reconfigure xserver-xorg" and selecting the "vesa" driver when asked (it will probably default to "ati").

---

