---
title: "discover installed wine, no wine command on menu"
date: 2021-11-03
forum: Wine
---

### Post by indianajo on 2021-11-03
PC has dual core Intel 2.73 ghz, 2 gb ram, 160 gb disk 95 gb left.  Lubuntu is amd64 vers 20.04.3
Discover program of menu/systemtools installed wine. No wine command appeared on menu. There are wine and wine64 executables in /lib/wine . I right clicked wine64 and made it trustable.  Double clicked wine64, nothing happened.  Game CD was in disk reader. 
instructions for games is "right click executable, pick wine to execute" When I do that it shows the menu, which doesn't have wine on it.  
Trying to run autorun.exe on disk1 of sid meiers CIvilization III CD for Windows98 windows 2000 windowsXT
games listing of wine forum shows this version as gold.  
Thanks.

---

### Post by monkeybrain20122 on 2021-11-03
The wine.desktop file is not accessible by default hence it is not showing up on the context menu. So just copy it to the right location 

```
sudo cp /usr/share/doc/wine/examples/wine.desktop /usr/share/applications
```

May need to logout and login again

---

### Post by indianajo on 2021-11-03
$ cannot create regular file/directory 'usr/share/applications': No such file or directory
It's lying to me, file manager can see usr/share/applications .  has a lot of logos of programs in there.  
in usr/share/doc there are folders for wine, wine32 and wine64 .
So there is no wine.desktop in usr/share/applications  Would one of the folders that are there do? Wine64 maybe? There are wine32server and wine64server which are obviously wrong for my desktop pc.  
In folders wine64, wine32 are no executables.  just some .gz s . In folder wine there are no executables, but in a subdirectory examples there is an executable named "wine windows program loader" ?
Thanks

---

### Post by deadflowr on 2021-11-03
You forgot the slash.
It's not usr, it's /usr.

---

### Post by indianajo on 2021-11-03
Thanks very much.  copied wine64 from /lib/wine to /usr/share/applications 
No error. File manager says it is there.  
Off on an adventure, reboot.
Edit after reboot, there is no wine64 on the menu anywhere.  wine64 executable is in the /usr/applications file . ?

---

### Post by deadflowr on 2021-11-03
Why didn't you simply follow the command given in post #2?

---

### Post by indianajo on 2021-11-03
There is no wine.desktop in /usr/share/doc/wine/examples/  .  discover did not put one there.  If there it is invisible. 
entered  string from post 2  again in terminal.  no error.  no wine.desktop executable in /usr/share/applications 
will reboot again.

---

### Post by deadflowr on 2021-11-03
Hmm, odd as it's a default file for wine package.
In a terminal run
```
dpkg -l | grep wine
```
posts the results.

---

### Post by indianajo on 2021-11-03
was no wine.desktop in /usr/share/doc/wine/examples/  only "wine windows program loader"
Typed the string in post #2 in the terminal again. no error this time, maybe I forgot a leading slash.  That copied "wine windows program loader" icon onto /usr/share/applications . After reboot, that command did not put a wine command on the menu.

---

### Post by deadflowr on 2021-11-03
It doesn't add a main menu item, it adds a right click context menu item.
If you click on a Windows app file and right click on it the wine program loader option should now be listed.
If that make sense.

---

### Post by indianajo on 2021-11-03
Rebooted, tried to right click autorun.exe on Civilization III CD . Option shows menu.  No wine on any menu category. 
typed dpkg -l | grep wine into terminal
got: 
```
ii-fonts-wine 5.0-3ubuntu1 all Windows api implementation -fonts
ii libwine:amd64 5.0-3ubuntu1 amd64 windows api implementation - library
ii libwine:i386  5.0-3ubuntu1 i386 windows api  implementation  - library
ii wine   5.0-3ubuntu1 all windows api implementation - standard suite
ii wine32:i386 5.0.3ubuntu1 i386 windows api implementation - 32-bit binary loader
ii wine64 5.0-3ubuntu1 amd windows api implementation -64-bit binary loader
```
 Thanks for looking

---

### Post by deadflowr on 2021-11-03
Sorry, it should be in the "open with" (or "open with other application") option.
Might need to be added, which means go to the open with other application option and scroll through the listing of apps that can be added.
Wine Program Loader would be at the very bottom.

---

### Post by Dennis N on 2021-11-04
So you have a CD. Is there an install program on the CD? 
I have a couple of XP programs on CD that run with wine. On each CD is an "install.exe" file. Right click on install.exe and choose "Open with Wine Windows Program Loader" . When it's done, you should have entries in the Applications Menu for the actual program. 

OR:

In terminal, you probably can just navigate to the CD-Rom, and run **wine install.exe** and that will work too, as below (it's an old program for astronomy): 

```
[dmn@Sydney DS_2_CDROM]$ ls -1
appsetup.inf
asteroid
comets
dst_suns
earth
**install.exe**
jupiter
mars
mercury
misc
moon
neptune
ngc
pluto
saturn
sun
uranus
venus
vistapro
[dmn@Sydney DS_2_CDROM]$ wine install.exe

```

This may still be necessary - long ago it was: You run **winecfg** in the terminal before doing anything else. This sets up the directories, and you can specify what kind of Windows you have and other things.

You can also install and use **playonlinux** to take care of the installation of Windows programs.

---

### Post by indianajo on 2021-11-04
> **deadflowr said:**
> Sorry, it should be in the "open with" (or "open with other application") option.
Might need to be added, which means go to the open with other application option and scroll through the listing of apps that can be added.
Wine Program Loader would be at the very bottom.
Well yes, when I right click on Civ III CD  autorun.exe in file manager,  I get "run with other applications". Then it shows me a picture of the menu with no wine on it anywhere.  No wine windows program loader.  No wine anything. Other option tab is "custom command" with a blank in the command line. then below it has a blank for name of application.  Am I supposed to type something in the custom command blank to add wine?   /usr/share/applications/"wine windows program loader" perhaps which is the file that moved? or maybe "/usr/share/applications/wine.desktop"  which is what moved the icon "wine windows program loader" ?
Edit, tried custom command tab of "run with other application" box (when right clicked civ III cd autorun.exe), typing /usr/share/applications/wine.desktop  in command box and wine in name box.  Nothing happened.  Then tried "/usr/share/applications/wine windows program loader" in command box, wine in name box, nothing happened.  Then tried "/usr/share/applications/'wine windows program loader'" in command box & wine in name box, nothing happened.
Mr Dennis N, civilization 3 CD autorun.exe has its own base menu which first allows installation, then later runs the game.  Trouble with running autorun.exe in qterminal, I don't know the name of the cd+dvd reader.  Been reading linux commandbook and he makes a big point of linux not having letters for drive names.  Ran qterminal "winecfg"  , got a lot of error messages about missing fonts.  Then a box came up, I was allowed to change windows type from 7 to xp, Because civilization III runs on win98, 2000, and xp only, not on win7.  There were a lot of other choices on that box I didn't understand.

---

### Post by monkeybrain20122 on 2021-11-04
This is my screenshot. Since you mentioned "Discover" you are using Kubuntu, no? I think by right clicking the .exe file and choose properties .. dolphin should show a list of applications but I don't have any KDE distro here to look at.

---

### Post by deadflowr on 2021-11-04
Go figure I wasn't even paying attention to Discover.
If using Kubuntu then you need to change the file's NoDisplay setting from true to false.
Something like
```
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /usr/share/applications/wine.desktop
```

should work.
The wine option would then be located in the Lost and Found section.
If you want it added to a specific category you would need to add the Category option to the desktop file.

---

### Post by Dennis N on 2021-11-04
> **indianajo said:**
> ...civilization 3 CD autorun.exe has its own base menu which first allows installation, then later runs the game.  Trouble with running autorun.exe in qterminal, I don't know the name of the cd+dvd reader.  Been reading linux commandbook and he makes a big point of linux not having letters for drive names.  Ran qterminal "winecfg"  , got a lot of error messages about missing fonts.  Then a box came up, I was allowed to change windows type from 7 to xp, Because civilization III runs on win98, 2000, and xp only, not on win7.  There were a lot of other choices on that box I didn't understand.

I see. My experience on Windows programs on CD is restricted to my own CDs. You are probably not using Ubuntu with Gnome desktop, so conditions are going to vary. I use an USB optical drive, and after inserting a CD, it shows in the side pane's Devices list and can then be browsed by the file manager or opened in the terminal. Good luck getting your program to run

I used **PlayOnLinux** to install Windows Adobe software and it worked - It shows Civilization 4 on it's menu (screenshot below), but note there is an "Install unlisted program" at the bottom if your program is not shown. That might be something you could look into. It's in Software.

---

### Post by indianajo on 2021-11-04
> **deadflowr said:**
> Go figure I wasn't even paying attention to Discover.
If using Kubuntu then you need to change the file's NoDisplay setting from true to false.
Something like
```
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /usr/share/applications/wine.desktop
```

should work.
The wine option would then be located in the Lost and Found section.
If you want it added to a specific category you would need to add the Category option to the desktop file.
qterminal command sed worked.  NoDisplay was changed to false. After that right clicking autorun.exe on the civ III disk brought up "load with wine windows program loader"  .  Problem solved. Was lubuntu20.4.3 which tag shows on the thread title but not on these entries for some reason. I can't click "solved" for some reason, no button. Thanks everybody.  
Load of program errored on disk 3, but that is another problem that probably can't be solved.  I really need to replace 100 capacitors in an old computer so I can reload win98.

---

### Post by deadflowr on 2021-11-04
> I can't click "solved" for some reason, no button.
You mean no "Mark this Thread as Solved..." in Thread Tools up top?

---

