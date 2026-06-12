---
title: "Cant Run Games?"
date: 2008-04-10
forum: Wine
---

### Post by cafeinoz on 2008-04-10
I have trouble when tring to run my favourite windows games. When I open them with Wine my screen goes black and I have to reboot.:confused:

---

### Post by ELF_O8 on 2008-04-10
Wine doesn't always work that well, especially if you want to run uber-graphics games.
Also, from my experience, Wine and KDE don't mix well, so if you are using Kubuntu, that could be the reason.

---

### Post by belda on 2008-04-10
it is bad, that the favourite ones, u r used to play dont work, but look on the bright side, there are few windows games which run on linux and that is pretty cool.

take a look at [http://appdb.winehq.org/](http://appdb.winehq.org/) and try posting your own experience

---

### Post by CarpKing on 2008-04-10
How are you running these games?  There's a sticky in this forum with a bunch of useful tips for how to start programs among other things, but basically double-clicking the exe isn't the best approach.  The program often has trouble finding its other files then, and may fail to start or start all black.  If the game is trying to start fullscreen, your screen will be black.  The best approach is to open the directory the game is installed in in a terminal and type "wine program.exe" or have a launcher that does this for you.  

If the black screen happens in the future, you probably don't have to reboot.  First try alt+tab (does the same thing as in windows).  This should work, but if it doesn't, try ctrl+alt+F1, which will dump you into a terminal where you can login and type "killall program.exe," hit enter, and then hit ctrl+alt+F7 to get back to the desktop.  If that fails, ctrl+alt+backspace will close all programs and put you back to the login screen without having to actually reboot the computer.

---

### Post by Kinst on 2008-04-10
Um...which games? Wine usually requires tweaking before you can install or run anything.

---

### Post by CarpKing on 2008-04-10
Oh also, did you type winecfg into a terminal after you installed wine?  You have to do that to make it set up the proper directories and such.

---

### Post by cafeinoz on 2008-04-10
I use Ubuntu (Gnome)

---

### Post by schtufbox on 2008-04-10
run winecfg, in the graphics options, make it use a virtual desktop (I usually use 1280x800) then when you run your game, if it hangs,  you can still see your desktop, and console to check what caused wine to hang (as far as the windows app/game is concerned it's running fullscreen but it's actually a window on the linux desktop).  Much better than using fullscreen and not being able to see anything.

Another option is the ctrl+alt+f1  login to the console there, type wineserver -k  to kill wine then ctrl+alt+f7 to get back to desktop and then check your console from there.

---

### Post by cogadh on 2008-04-10
> **cafeinoz said:**
> I have trouble when tring to run my favourite windows games. When I open them with Wine my screen goes black and I have to reboot.:confused:
It would really help if you gave some useful information, such as what games you are trying to run, how you have Wine configured, what kind of hardware you have, how you run the games, etc. Without telling us much more than "my game won't work", we can't really help.

> **ELF_O8 said:**
> Wine doesn't always work that well, especially if you want to run uber-graphics games.
Wine runs most DirectX 9 or older games nearly perfectly. I run literally dozens of  games in Wine quite successfully (all the HL2 games, Hitman games, KotOR games and Call of Duty games, just to name a few).
> Also, Wine and KDE don't mix well, so if you are using Kubuntu, that could be the reason.
Huh? I've been using Wine with KDE for years. Its no better or worse than using it with Gnome.

---

### Post by cafeinoz on 2008-04-11
> **schtufbox said:**
> run winecfg, in the graphics options, make it use a virtual desktop (I usually use 1280x800) then when you run your game, if it hangs,  you can still see your desktop, and console to check what caused wine to hang (as far as the windows app/game is concerned it's running fullscreen but it's actually a window on the linux desktop).  Much better than using fullscreen and not being able to see anything.

Another option is the ctrl+alt+f1  login to the console there, type wineserver -k  to kill wine then ctrl+alt+f7 to get back to desktop and then check your console from there.

Thanks for the idea but its set to 640x480 and i cant reach the apply button. i have tried reinstalling but its still the same settings

---

### Post by CarpKing on 2008-04-12
After you select the height for the new size, with that field still selected hit enter.  I've run into this issue before, and I think that's how I solved it.  Failing that there's probably a config file somewhere in ~/.wine that you could edit, but make sure it is what you think it is before you change anything.

---

### Post by cogadh on 2008-04-12
Open the ~/.wine/user.reg file with a text editor and scroll all the way down to the bottom. You should see a section that looks something like this:
```
[Software\\Wine\\X11 Driver] 1208032951
"Desktop"="640x480"
```
Change the "640x480" to at least "800x600" and you will be able to access all the buttons in winecfg again.

---

