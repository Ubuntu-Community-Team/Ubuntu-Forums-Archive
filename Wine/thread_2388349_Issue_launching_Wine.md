---
title: "Issue launching Wine"
date: 2018-03-31
forum: Wine
---

### Post by moto1860 on 2018-03-31
According to ubuntu software I've both Wine and Wine development version installed (can't find them under show applications tho) however clicking on them from there and then *Launch *nothing happens, why is that?

```
avo@avo-Latitude-E5430-non-vPro:~$ wine --versionwine-2.18 (Ubuntu 2.18-1)



```

---

### Post by kc1di on 2018-04-01
Wine does not normally launch like other apps.  It launches with command line commands such as winecfg.  It has no real gui to launch.  
If you want a gui version I would suggest you install playonlinux which is a nice gui for wine.  and even allows you to install newer or older versions of wine side by side. 
This is handy as some apps work better on older and some on newer versions. It also seperates the installs somewhat from the rest of the system by using virtual files so that
it will not affect other apps you have installed. Good Luck.

---

### Post by Dennis N on 2018-04-01
> **moto1860 said:**
> According to ubuntu software I've both Wine and Wine development version installed (can't find them under show applications tho) however clicking on them from there and then *Launch *nothing happens, why is that?


Wine needs the program name (with path to executable) as an argument. Example from my computer:
```
wine /home/dmn/.wine/drive_c/"Program Files/Litsoft/Across Lite/ACROSSL.EXE" 
```
will start the ACROSSL.EXE program when run in terminal.

This same command is used in the EXEC= line of the program's desktop file to provide a menu entry:

```
[Desktop Entry]
Version=1.0
Type=Application
Name=Across Lite
Comment=Play Crossword Puzzles
Exec=wine home/dmn/.wine/drive_c/"Program Files/Litsoft/Across Lite/ACROSSL.EXE"
Icon=/home/dmn/.icons/acl3.png
Path=/home/dmn/.wine/drive_c/"Program Files/Litsoft/Across Lite/"
Categories=Game;
Terminal=false
StartupNotify=false
```

---

