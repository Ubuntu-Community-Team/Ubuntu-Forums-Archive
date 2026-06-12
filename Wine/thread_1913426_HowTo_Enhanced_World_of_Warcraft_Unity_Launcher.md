---
title: "HowTo: Enhanced World of Warcraft Unity Launcher"
date: 2012-01-22
forum: Wine
---

### Post by infernoid on 2012-01-22
I was inspired by [http://www.techdrivein.com/2011/05/top-6-quicklists-for-ubuntu-1104-natty.html](http://www.techdrivein.com/2011/05/top-6-quicklists-for-ubuntu-1104-natty.html) so I made myself a new custom launcher for world of warcraft.
Hope you guys enjoy it :D

[LEFT][IMG]http://ubuntuforums.org/attachment.php?attachmentid=211310&stc=1&d=1327260306[/IMG]
[/LEFT]
 
Features:

[LIST]
[*]Work around recent launching problems (Launcher not starting WoW)
[*]Add easy access to AddOns Folder and World of Warcraft Repair
[*]Stop creating world of warcraft icon over and over by Launcher.exe
[/LIST]
 Press CTRL+ALT+T to open a terminal and enter following command:
```
gedit ".local/share/applications/wine/Programs/World of Warcraft/World of Warcraft.desktop"
```Edit the desktop launcher in gedit and save
```
[Desktop Entry]

Name=World of Warcraft
Comment=Click here to play World of Warcraft.
Icon=0B22_Launcher.0
Exec=wine "C:/Program Files/World of Warcraft/Wow.exe"
Terminal=false
StartupNotify=true
Type=Application
OnlyShowIn=GNOME;Unity;
Name[en_US]=World of Warcraft

X-Ayatana-Desktop-Shortcuts=Launcher;AddOns;Repair

[Launcher Shortcut Group]
Name=Launcher
Exec=env WINEDLLOVERRIDES="winemenubuilder.exe=d" wine "C:/Program Files/World of Warcraft/Launcher.exe"
TargetEnvironment=Unity

[AddOns Shortcut Group]
Name=AddOns
Exec=nautilus ".wine/drive_c/Program Files/World of Warcraft/Interface/AddOns"
TargetEnvironment=Unity

[Repair Shortcut Group]
Name=Repair
Exec=wine "C:/Program Files/World of Warcraft/Repair.exe"
TargetEnvironment=Unity
```Open unity dash and search for world of warcraft. Drag the "World of Warcraft" to your task bar. Enjoy the new fancy unity world of warcraft launcher :D

---

### Post by ergo-proxy on 2012-01-23
Very nice :)
 
You might also want to add wineprefix to your launcher:
 
Exec=env WINEPREFIX="/home/user/.wineprefixes/.wine-wow" wine C:\\\\Program\\ Files\\\\World\\ of\\ Warcraft\\\\Wow.exe

---

### Post by merc669 on 2012-06-30
I have moved my WOW directory to my "/home/merc669/"World of Warcraft" directory. All of these point to the "C"drive on Windows. How can I change this to point to the home directory vice the "C" drive so it shows up on my Unity Launcher bar? Still new at this but do have it running fine with wine! Thanks!!!

Bill....

---

### Post by Dlambert on 2012-06-30
Very well made. Any chance for a Diablo III Launcher? ;)

---

