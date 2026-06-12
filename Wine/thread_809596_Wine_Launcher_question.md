---
title: "Wine Launcher question?"
date: 2008-05-27
forum: Wine
---

### Post by Ioky on 2008-05-27
I have a software install with wine, Wine give me a icon on the Desktop which run perfectly, however, when I try to set up a launcher for software in the menu by using the same command like the one on the Desktop have. it doesn't work. Don't know why. I can't run the software with Shell neither, but I can run it by directly click on the EXE at the location it was installed.


env WINEPREFIX="/home/usrname/.wine" wine "C:\Path To EXE File\XXX.EXE" 

I try this, but it doesn't work. which is what the one in the Desktop use.

Can some one help?

---

### Post by ajackson on 2008-05-27
Has the directory path got spaces in it?

If so you either need to enclose the entire path in quotes or escape the spaces, i.e. Program Files becomes Program\ Files

---

### Post by Ioky on 2008-05-27
No it doesn't have any space.

the same path work on the Desktop Icon, just no the one in the Menu on the Panel

Any Idea?

---

