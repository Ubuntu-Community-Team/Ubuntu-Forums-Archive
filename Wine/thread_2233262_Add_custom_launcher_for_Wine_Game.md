---
title: "Add custom launcher for Wine Game"
date: 2014-07-07
forum: Wine
---

### Post by kakashi_12 on 2014-07-07
I just installed LFS (Live For Speed) via Wine. It opens fine. But when I try to add it to the Applications, Games menu, it won't open.
It just shows some error asking if it's installed correctly. Only option is ok.
I browsed to the path and file. I can open it directly from Window Manager, but not here.
Is there some command I have to add to get it to run in Wine?

---

### Post by Dennis N on 2014-07-07
You don't mention what OS you are using, but on my Xubuntu system, Wine creates its own main menu category and puts launchers in there (sometimes). Otherwise, I make a .desktop file and place it in ~/.local/share/applications. That puts it into the main menu under whatever category I specify (Games in the example below).

Be sure the Exec= line is correct and begins with wine.

Example of .desktop file:

```
[Desktop Entry]
Version=1.0
Type=Application
Name=Across Lite
Comment=Play Crossword Puzzles
Exec=wine "c:\program files\Litsoft\Across Lite\ACROSSL.EXE"
Icon=/home/dmn/.icons/acl.png
Categories=Game;
Terminal=false
StartupNotify=false
```

---

### Post by kakashi_12 on 2014-07-07
Sorry. Ubuntu 14.04 Trusty Tahr 64 bit.

---

### Post by Dennis N on 2014-07-07
No difference. It works the same in Ubuntu (Unity). I have that same example program in post #2 on my Ubuntu 12.04 as well. I can put a launcher on the Desktop, and it also appears in the Classic Menu Indicator under Games, or in the Dash search.

To get a launcher on the Desktop, just copy the .desktop file to your Desktop folder.

---

### Post by kakashi_12 on 2014-07-08
Didn't work. Same error "Could not write to data folder. Is LFS correctly installed on a hard drive?"

---

### Post by kakashi_12 on 2014-07-08
Got it. Uninstalled via Wine and re-installed. This time I checked the options for "Create desktop icon" and "Create start menu icon".
I had them unchecked last time because they don't exist. So I just copied the command for the launcher over to my custom launcher.
Command actually read as this:
env WINEPREFIX="/home/user/.wine" wine C:\\windows\\command\\start.exe /Unix /home/user/.wine/dosdevices/c:/users/user/Start\ Menu/Programs/Live\ for\ Speed/LFS.lnk

---

### Post by Dennis N on 2014-07-08
As a test that the command is right, start it from the terminal with the identical command used in the Exec= line. It should start up. Using my example program in post #2:
In the terminal:
```
dmn@Roxanne:~$ wine "c:\program files\Litsoft\Across Lite\ACROSSL.EXE"
```
will start that program. 

Since it complains about the data folder, this might also be necessary:
Put another line **Path=** in the .desktop file (after Exec=) with the full path to the program's data folder.

Edit:
Missed the last post you made as I left the editor for a half hour, then posted. Glad you got it working!

---

### Post by Dennis N on 2014-07-08
Just to add, this is interesting:

The wine installer created this command for the program in post #2 when it created the application menu entry:
```
env WINEPREFIX="/home/dmn/.wine" wine C:\\windows\\command\\start.exe /Unix /home/dmn/.wine/dosdevices/c:/users/dmn/Start\ Menu/Programs/Across\ Lite.lnk

```
But the simpler command:
```
wine "c:\program files\Litsoft\Across Lite\ACROSSL.EXE"
```
also works (and is understandable).

---

