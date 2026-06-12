---
title: "Wine prefix"
date: 2011-12-15
forum: Wine
---

### Post by new to linux help needed on 2011-12-15
how would i create a new wine prefix? is it the code 
WINEPREFIX /home/<USERNAME>/.... wine?
what is the code for installing stuff on that new wine prefix. thanks =)

---

### Post by BC59 on 2011-12-15
The easiest way is to rename the hidden /.wine folder on /home directory.

---

### Post by cwwilson721 on 2011-12-15
The way I do it (Using World of Warcraft as an example):

[LIST]
[*]Install as usual to the default '.wine' folder (My /home/<USER>/.wine folder is only for installing new stuff, just for this). Created by deleting .wine, then recreated with winecfg
[*]After a successful install.. a launcher would usually be created, with the command (in 'Properties' of the launcher) of something like ```
[COLOR="Blue"]env WINEPREFIX=[/COLOR]"/home/<USER>/[COLOR="red"].wine[/COLOR]" wine "C:\Program Files\World of Warcraft\Wow.exe" -opengl
```
[*]I then rename the .wine folder to something like .wine-wow
[*]I then edit the launch command to something like ```
[COLOR="blue"]env WINEPREFIX=[/COLOR]"/home/<USER>/[COLOR="Red"].wine-wow[/COLOR]" wine "C:\Program Files\World of Warcraft\Wow.exe" -opengl
```
[/LIST]

Note the use of the command '[COLOR="Blue"]env WINEPREFIX=[/COLOR]' part, and the change of the [COLOR="Red"]installed wine folder[/COLOR] for this program. That puts the program in a 'sandbox' that can run with another wine program in another 'sandbox' and different [COLOR="Red"]install folder[/COLOR], without 'mixing' the two. Just using WINEPREFIX alone doesn't accomplish this as fully.

As to the other posters comment:
[QUOTE=BC59]The easiest way is to rename the hidden /.wine folder on /home directory.[/QUOTE]
[COLOR="SeaGreen"]This AIN'T gonna do squat but make the program not run.[/COLOR]

---

### Post by BC59 on 2011-12-16
> **cwwilson721 said:**
> 
[COLOR="SeaGreen"]This AIN'T gonna do squat but make the program not run.[/COLOR]

If you have a program inside - yes. He just asked how to create a new Wineprefix.

---

