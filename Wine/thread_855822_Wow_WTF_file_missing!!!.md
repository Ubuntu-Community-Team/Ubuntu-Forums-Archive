---
title: "Wow WTF file missing!!!???"
date: 2008-07-10
forum: Wine
---

### Post by jean9120 on 2008-07-10
I just installed wow on my laptop and i have an ati card in it and need to change the wtf file to get wow to work at all. The installation went fine without any errors, and ive tried viewing hidden files but there arnt any. What can i do??

---

### Post by Muffinabus on 2008-07-10
Run the game so that it creates the files.

---

### Post by jean9120 on 2008-07-11
i would but the game wont open for some reason after all of the instalations were successfull.

---

### Post by webbed on 2008-07-13
I suspect that your World or Warcraft game is crashing on the start up movies, I would recommend creating a blank WTF file and adding the following lines to is:

SET movie "0"
SET expansionMovie "0"
SET gxApi "OpenGL"

When I tried deleting the config.wtf file to create a new one (game was working previously) it would not do so either. The config.wtf file must be created in the WTF folder or your World of Warcraft install directory.

WoW should add all of the rest of the necessary lines to the config file.

---

### Post by flytripper on 2008-07-14
> **webbed said:**
> I suspect that your World or Warcraft game is crashing on the start up movies, I would recommend creating a blank WTF file and adding the following lines to is:

SET movie "0"
SET expansionMovie "0"
SET gxApi "OpenGL"

When I tried deleting the config.wtf file to create a new one (game was working previously) it would not do so either. The config.wtf file must be created in the WTF folder or your World of Warcraft install directory.

WoW should add all of the rest of the necessary lines to the config file.

this fixed my install too..

---

### Post by Chris1511 on 2008-07-24
I did as you said and now it does not play the intro's and all i can see on the screen is a square and a bar the square seems to be the icon.

Any help please:confused:

---

### Post by flytripper on 2008-07-24
try making a clean wtf file with just this: SET gxApi "OpenGL"

let us know what happens

---

### Post by thisismalhotra on 2008-07-24
Follow this tutorial and everything should be fine (Ati card .. so may take a bit of effort)

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by Chris1511 on 2008-07-24
Thanks that tutorial worked finally all reasons to use windows are gone :)

---

