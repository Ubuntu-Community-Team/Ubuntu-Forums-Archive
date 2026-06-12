---
title: "Wine shortcut for Hearts of Iron III does not work"
date: 2013-08-29
forum: Wine
---

### Post by user_of_gnomes on 2013-08-29
I can't for the life of me get the below shortcut to work (13.04 Gnome 3)

```
[Desktop Entry]
Name=Hearts of Iron III Collection
Exec=env WINEPREFIX="/home/user/.wine_hoi3_32bit" wine C:\\\\windows\\\\command\\\\start.exe /Unix /home/user/.wine_hoi3_32bit/dosdevices/c:/users/Public/Start\\ Menu/Programs/Hearts\\ of\\ Iron\\ III\\ Collection/Hearts\\ of\\ Iron\\ III\\ Collection.lnk
Type=Application
StartupNotify=true
Path=/home/user/.wine_hoi3_32bit/dosdevices/c:/Games/Paradox Interactive/Hearts of Iron III Collection
Icon=AD37_hoi3.0
```

It was automatically created by Wine and although it starts Wine, it doesn't do much beyond that except shutting it down again.
The game works if I invoke it through the terminal but not through the shortcut.

I can't troubleshoot this shortcut because you can't seem to execute shortcuts from the terminal and therefore I have no output to work with.
Does anybody know how I can get some kind of error log from the shortcut so I can troubleshoot whatever is wrong with it?

There is another shortcut created by Wine for Steam which, although affecting a different wineprefix (the default), works fine.

---

### Post by Toz on 2013-08-29
> I can't troubleshoot this shortcut because you can't seem to execute shortcuts from the terminal and therefore I have no output to work with.
Does anybody know how I can get some kind of error log from the shortcut so I can troubleshoot whatever is wrong with it?
Run the executable command that follows "Exec=" to see what errors you get:
```
env WINEPREFIX="/home/user/.wine_hoi3_32bit" wine C:\\\\windows\\\\command\\\\start.exe /Unix /home/user/.wine_hoi3_32bit/dosdevices/c:/users/Public/Start\\ Menu/Programs/Hearts\\ of\\ Iron\\ III\\ Collection/Hearts\\ of\\ Iron\\ III\\ Collection.lnk
```
> The game works if I invoke it through the terminal but not through the shortcut.
You can always change the "Exec=" line to run the command that works on the terminal.

---

### Post by user_of_gnomes on 2013-08-30
Thanks for the hints! I learnt more about the problem but nothing has lead to a fix.
I give up on trying to launch it from the shortcut printed above, I have tried installing it in a different location (C:\hoi3) to see if that was the problem but that yields the same result: 

```
fixme:exec:SHELL_execute flags ignored: 0x00000100
Application could not be started, or no application associated with the specified file.
ShellExecuteEx failed: Success.

```

Adjusting the shortcut to reflect the command I use from the terminal would be acceptable but there's a catch:

If I use env WINEPREFIX=$HOME/.wine_hoi3_32bit wine hoi3game.exe, the game works fine.
However it does require me to first manually navigate to the directory that the executable resides in! 

If I launch the application using env WINEPREFIX=$HOME/.wine_hoi3_32bit wine $HOME/.wine_hoi3_32bit/drive_c/Games/Paradox\ Interactive/Hearts\ of\ Iron\ III\ Collection/hoi3game.exe Wine states that "the working directory doesn't seem to be correct"

What am I doing wrong?

---

### Post by Toz on 2013-08-30
> If I use env WINEPREFIX=$HOME/.wine_hoi3_32bit wine hoi3game.exe, the game works fine.
However it does require me to first manually navigate to the directory that the executable resides in! 
Try to create a launcher script. Something like this (lets call it **hoi** in your home directory):
```

#!/bin/bash
cd $HOME/.wine_hoi3_32bit/drive_c/Games/Paradox\ Interactive/Hearts\ of\ Iron\ III\ Collection
env WINEPREFIX=$HOME/.wine_hoi3_32bit wine hoi3game.exe
```
...make the script executable:
```
chmod +x $HOME/hoi
```
...then in the desktop file, set:
```
Exec=/home/user/hoi
```

> 
If I launch the application using env WINEPREFIX=$HOME/.wine_hoi3_32bit wine $HOME/.wine_hoi3_32bit/drive_c/Games/Paradox\ Interactive/Hearts\ of\ Iron\ III\ Collection/hoi3game.exe Wine states that "the working directory doesn't seem to be correct"
Try replacing $HOME with the actual expanded directory path. Maybe its not processing $HOME.

---

### Post by user_of_gnomes on 2013-08-31
Thanks a lot for the help! 

I've been writing a step-by-step guide on how to get Hearts of Iron III to work with Wine and the problem of not having a functioning shortcut has had me doing research and experimenting for well over 5 hours but the shortcut works. FINALLY!
Hopefully it'll save someone else a whole lot of headache and frustration when I put the guide up.

> 
Try replacing $HOME with the actual expanded directory path. Maybe its not processing $HOME. 

Oddly enough that doesn't work either. Neither does using ~ instead of $HOME.
I wonder if it's a problem with HOI3 itself, Judging from search results the same error pops up when a modification is installed that doesn't have all the right paths set ... 
Unfortunately, I can't find out where to change these settings in an unmodified game.

---

