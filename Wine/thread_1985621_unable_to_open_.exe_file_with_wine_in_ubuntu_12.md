---
title: "unable to open .exe file with wine in ubuntu 12"
date: 2012-05-23
forum: Wine
---

### Post by Nadarasan on 2012-05-23
I have installed wine windows interface program to open .exe files but I am unable to open .exe file using wine in ubuntu 12.Please suggest solutions.

---

### Post by roelforg on 2012-05-23
Right click on the exe and click on properties
Now go to permissions and click the on "make this file executable"
Click ok and try again

---

### Post by donkyhotay on 2012-05-23
> **roelforg said:**
> Right click on the exe and click on properties
Now go to permissions and click the on "make this file executable"
Click ok and try again

This will probably work for the most common reason wine applications won't run (permissions). If this doesn't work for you then you'll need to post exactly *how* you are trying to open the .exe file. Be aware linux is different from windows, by default just "double-clicking on the icon" won't work with standard permissions which are set that way to be more secure. If you're new (and no offense but it sounds like you are from your post and post count) then I would recommend installing playonlinux and using that. It's a front-end for wine that makes it a lot easier to install and run windows programs (and wouldn't need messing with permissions for .exe files). If you insist on using straight wine then I would recommend using the CLI (terminal), especially when trying to set up or install a program for the first time. Wine can be pretty unstable and using the CLI will at least give you a crash dump if things go wrong that you can copy and paste onto the forums for better assistance.

---

### Post by roelforg on 2012-05-23
> **donkyhotay said:**
> This will probably work for the most common reason wine applications won't run (permissions). If this doesn't work for you then you'll need to post exactly *how* you are trying to open the .exe file. Be aware linux is different from windows, by default just "double-clicking on the icon" won't work with standard permissions which are set that way to be more secure. If you're new (and no offense but it sounds like you are from your post and post count) then I would recommend installing playonlinux and using that. It's a front-end for wine that makes it a lot easier to install and run windows programs (and wouldn't need messing with permissions for .exe files). If you insist on using straight wine then I would recommend using the CLI (terminal), especially when trying to set up or install a program for the first time. Wine can be pretty unstable and using the CLI will at least give you a crash dump if things go wrong that you can copy and paste onto the forums for better assistance.

If i use wine, i only launch via cli when the prog won't start.
If i'm missing a dll, the console will tell me but i usually have enough dll files.

---

### Post by oldos2er on 2012-05-23
Thread moved to Wine.

---

