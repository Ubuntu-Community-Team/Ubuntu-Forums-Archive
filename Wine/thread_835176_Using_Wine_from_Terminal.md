---
title: "Using Wine from Terminal"
date: 2008-06-20
forum: Wine
---

### Post by BlackSwordD2 on 2008-06-20
well i've looked around and i've seen constant messages about it but i simply dont know how to run it with a GUI.

if nothing else i'd like a general formula for running the apps

such as $ wine _____________

and if anyone is feeling extra generous maybe a general formula for installing start to finish?

---

### Post by Rhubarb on 2008-06-20
Programs that run in wine are generally kept in your home directory:
~/.wine/drive_c/Program Files/

So as an example, to run Quake2 in wine (after the app has been installed with wine):
```
cd ~/.wine/drive_c/Program\ Files/id\ software/Quake\ II/
wine quake2.exe
```

To run / install an windows application.exe on your Desktop:
```
cd ~/Desktop
wine application.exe
```

Some windows programs that you have installed with wine appear in Applications --> Wine --> Programs
Sometimes it's also possible to install / run windows applications by double clicking on the exe on your Desktop or in the Nautilus file manager.

---

### Post by BlackSwordD2 on 2008-06-20
what do i do when i try to install an app in the terminal and it gives me the message "Module not found"?

---

### Post by Rhubarb on 2008-06-20
Does it tell you what module is not found?

In some cases wine is missing a .dll file that a program needs for it to run.  In those cases sometimes it's possible to tell wine (look in winecfg:  Applications --> Wine --> Configure Wine) to use a .dll file from windows (if you have windows installed on a partition, grab the dll you need from there in your C:\Windows\System32 folder, otherwise search for the dll on the net).

---

