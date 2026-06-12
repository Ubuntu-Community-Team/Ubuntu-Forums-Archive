---
title: "I can't undo a mistake with Winecfg"
date: 2008-04-29
forum: Wine
---

### Post by Iago1989 on 2008-04-29
I made the display 600X400...bad move! I had no idea I'd have normal resolution I.E. windows in a 600X400 space, and even worse, WINECFG looks like this

[IMG]http://i108.photobucket.com/albums/n2/Dasquirrel/wine.jpg[/IMG]

And I can't scroll! I can't go down to edit the resolution or screen size!

I've uninstalled Wine using the add/remove, I've reinstalled using add/remove, I've installed the version in the "how to get the latest Wine" thing in this forum using the terminal, none of which resets my winecfg! Please help!

I'm using ubuntu 8.04

---

### Post by fs3rp4 on 2008-04-29
Delete the .wine directory from your home. With this all Wine configurations will be lost.

---

### Post by cogadh on 2008-04-29
If you have applications already installed that you want to save, then instead of deleting the .wine directory, you can manually edit Wine's registry files. Using a text editor (Gedit, Kate or Nano, **not** OpenOffice), open the ~/.wine/user.reg file and scroll all the way to the bottom for an entry that looks like this:
```
[Software\\Wine\\X11 Driver] 1209401998
"Desktop"="600X400"
```
Either change the "600X400" to "800X600" to set the virtual desktop to a manageable size or delete the entire "Desktop" line to restore Wine to full screen operation (don't delete the "[Software\\Wine\\X11 Driver] 1209401998" line).

To fix the font size issue, open the ~/.wine/system.reg file with a text editor and look for this section:
```
[System\\CurrentControlSet\\Hardware Profiles\\Current\\Software\\Fonts] 1209080331
"FIXEDFON.FON"="vgafix.fon"
"FONTS.FON"="vgasys.fon"
"LogPixels"=dword:00000060
"OEMFONT.FON"="vgaoem.fon"
```
The important line is **"LogPixels"=dword:00000060**. I'm not sure what yours will say, but if you change yours to match that line, font size will be reset to 96 DPI (which is what it normally is).

---

### Post by Iago1989 on 2008-04-29
okay so maybe this is my newbiness showing...but I can't find the .wine directory in my home folder, nor can I find this ~/.wine/user.reg thing using the terminal or the search function or anything...if this is too newbie for you guys to deal with I can ask it in the absolute begginers section :-P

---

### Post by fs3rp4 on 2008-04-29
> **Iago1989 said:**
> okay so maybe this is my newbiness showing...but I can't find the .wine directory in my home folder, nor can I find this ~/.wine/user.reg thing using the terminal or the search function or anything...if this is too newbie for you guys to deal with I can ask it in the absolute begginers section :-P

In Nautilus type CTRL+H and  you will see the hidden directories. Delete the .wine

---

### Post by Iago1989 on 2008-04-29
Looks like that worked. I guessed nautilus was the file browser :-P THanks for being nooob-friendly

---

