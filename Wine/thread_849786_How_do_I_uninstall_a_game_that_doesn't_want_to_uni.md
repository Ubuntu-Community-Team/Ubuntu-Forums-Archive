---
title: "How do I uninstall a game that doesn't want to unistall?"
date: 2008-07-04
forum: Wine
---

### Post by LinuxFox on 2008-07-04
I've been trying Wine on some of my Windows games experimenting, and the only one that worked was Quake 3.  I uninstalled the ones that didn't work via the "Uninstall Wine Software" option, and they uninstall.  

One game just doesn't want to uninstall.  Specifically an old Jimmy Neutron PC game from 2002, whenever I choose unistall from the Programs folder or the Wine Uninstall option, I keep getting an uninst.isu is corrupted message.

Is there any way of uninstalling it without messing up Wine?  I don't want to keep it in taking up disk space if it doesn't work (not a big deal for any game since I dual-boot Ubuntu and Windows XP).  Any help would be great?  Thanks in advance.

---

### Post by scragar on 2008-07-04
just use wine to veiw the folder, find where it was installed to and delete the folder, then you'll want to edit the menu(right click it and choose edit) and remove the launchers for the game. It's not a perfect solution, since there's a few files left and such, but it's better than the alternatives.

---

### Post by LinuxFox on 2008-07-04
Ok, before I do this I want to know, will it also remove the game from the Uninstall Wine Software list?  Just want to know if this will do anything since I know you have to use Uninstall on Windows instead of deleting it.

---

### Post by scragar on 2008-07-04
you can remove that option by removing the chunk from the equivalent to the windows registry:
```
gedit ~/.wine/system.reg
```
then find and remove the block for your game, the block looks like this```
[Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall\\Depths of Peril_is1] 1214938554
"DisplayName"="GAME version"
"HelpLink"="http://www.xxx.com/"
"Inno Setup: App Path"="C:\\Program Files\\GAME"
"Inno Setup: Deselected Tasks"="desktopicon"
"Inno Setup: Icon Group"="GAME"
"Inno Setup: Selected Tasks"=""
"Inno Setup: Setup Version"="5.1.14"
"Inno Setup: User"="scragar"
"InstallDate"="20080704"
"InstallLocation"="C:\\Program Files\\GAME\\"
"NoModify"=dword:00000001
"NoRepair"=dword:00000001
"Publisher"="someone"
"QuietUninstallString"="\"C:\\Program Files\\GAME\\unins000.exe\" /SILENT"
"UninstallString"="\"C:\\Program Files\\GAME\\unins000.exe\""
"URLInfoAbout"="http://www.xxx.com/"
"URLUpdateInfo"="http://www.xxx.com/"

```

---

### Post by LinuxFox on 2008-07-04
It worked both the game and uninstall options are gone.  Thanks a lot for your help. :)

---

