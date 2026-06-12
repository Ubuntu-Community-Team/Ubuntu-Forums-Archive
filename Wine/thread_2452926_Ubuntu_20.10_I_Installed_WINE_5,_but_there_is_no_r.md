---
title: "Ubuntu 20.10 I Installed WINE 5, but there is no right-click option"
date: 2020-10-30
forum: Wine
---

### Post by keith47 on 2020-10-30
I installed **WINE 5** via the apt installer. I configured **WINE** and all the windows programs I have installed run great and I can use the Ubuntu launcher to launch them. The problem is that in the ***"FILES"*** program when I right click a file to launch an executable ***(*.exe) ***in WINE there is no option to launch the program with **WINE**. Thanks for any solutions you can provide.

---

### Post by CatKiller on 2020-10-30
For reasons I never understood, the Wine devs stopped enabling by default  the .desktop files that provide that function. The solution is to copy those files from whichever examples directory they get put in to, I think, /usr/share/applications. You might need to log out and log back in afterwards.

---

### Post by bigmeme2 on 2020-12-28
You should try moving them over to Lutris. Lutris is basically a wine wrapper, and you can add .desktop shortcuts through that.

---

