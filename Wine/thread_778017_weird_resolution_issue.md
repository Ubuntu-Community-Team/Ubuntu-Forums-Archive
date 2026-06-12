---
title: "weird resolution issue"
date: 2008-05-01
forum: Wine
---

### Post by robobobatron on 2008-05-01
for whatever reason (i was hoping someone could tell me) my resolution is huge but only within wine. on my regular desktop resolution is fine. what did i do wrong and what can i do to fix it?
[IMG]http://i146.photobucket.com/albums/r269/robobobatron/oopsibrokeit.png[/IMG]

---

### Post by cogadh on 2008-05-01
Manually edit Wine's registry files. Using a text editor (Gedit, Kate or Nano, **not** OpenOffice), open the ~/.wine/system.reg file and look for this section:
```
[System\\CurrentControlSet\\Hardware Profiles\\Current\\Software\\Fonts] 1209080331
"FIXEDFON.FON"="vgafix.fon"
"FONTS.FON"="vgasys.fon"
"LogPixels"=dword:00000060
"OEMFONT.FON"="vgaoem.fon"
```
The important line is **"LogPixels"=dword:00000060**. I'm not sure what yours will say, but if you change yours to match that line, font size will be reset to 96 DPI (which is what it normally is).

---

### Post by robobobatron on 2008-05-02
i am a complete gnome newbie can you tell me what the ~ folder could be

edit: i believe i have found the folder but there is no . before the wine was that a mistake or am I in the wrong folder. if i am it woudl aslo explain why the file dose not reside within it

i found the file but the lines of code yo specified are in it no where

edit: the problem has been solved

thank you

---

### Post by cogadh on 2008-05-02
Just in case anyone else runs into the same issues you did, "~/" is terminal shorthand for indicating "the current user's home folder". The .wine directory does have a "." in front of it, but that makes it a hidden directory, so if you were looking for the file using the GUI file browser, you won't see it unless you show hidden files and folders.

The easiest way to edit the file without having to go to all the trouble of looking for it first, is to just use the terminal and type:
```
gedit ~/.wine/system.reg
```
or (for the Kubuntu users):
```
kate ~/.wine/system.reg
```
or to edit it directly in the terminal, no matter which 'buntu version you have:
```
nano ~/.wine/system.reg
```

---

### Post by earther on 2008-05-24
> **cogadh said:**
> Manually edit Wine's registry files. Using a text editor (Gedit, Kate or Nano, **not** OpenOffice), open the ~/.wine/system.reg file and look for this section:
```
[System\\CurrentControlSet\\Hardware Profiles\\Current\\Software\\Fonts] 1209080331
"FIXEDFON.FON"="vgafix.fon"
"FONTS.FON"="vgasys.fon"
"LogPixels"=dword:00000060
"OEMFONT.FON"="vgaoem.fon"
```
The important line is **"LogPixels"=dword:00000060**. I'm not sure what yours will say, but if you change yours to match that line, font size will be reset to 96 DPI (which is what it normally is).
At my resolution , the system font size is too small. How can I make it bigger?  The setting in my Wine registry is already as you suggested.

---

### Post by cogadh on 2008-05-24
Run winecfg, go to the Graphics tab and move the Screen resolution slider up to something higher. Don't go too high or you'll end up with a problem like the OP.

---

### Post by earther on 2008-05-24
Nope. That had no effect on the Wine system default font.  Bummer . . . What am i missing here?

---

### Post by cogadh on 2008-05-24
Are you sure you are changing the right setting? I just tested it on my system and it definitely changed the font size in winecfg.

---

### Post by schtufbox on 2008-05-24
> **earther said:**
> Nope. That had no effect on the Wine system default font.  Bummer . . . What am i missing here?

sudo apt-get install msttcorefonts 

might be it

---

### Post by earther on 2008-05-24
> **schtufbox said:**
> sudo apt-get install msttcorefonts 

might be it
Already did that when I installed.

---

