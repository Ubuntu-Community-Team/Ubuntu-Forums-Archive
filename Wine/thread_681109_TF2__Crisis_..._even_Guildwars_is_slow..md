---
title: "TF2 / Crisis ... even Guildwars is slow."
date: 2008-01-28
forum: Wine
---

### Post by ODF on 2008-01-28
Drivers are installed, tryed on wine or cedega ... but games like oblivion, bioshock crisis etc etc are really slow on my machine while in windows these games are fast.

I can't even play TF2, and guildwars I get 20 fps.

I know games would be slower but THAT much ... ? is that normal.

My video card is a En8800 GTS wich should be way enough to play these games ... even crisis. I play TF2 on 32 players servers full full with AA and its 30+ fps.

I really want to quit windows but it seams like it wont ...

---

### Post by upbeat.linux on 2008-01-29
What version of wine are you running?

---

### Post by eljoeb on 2008-01-29
Seems normal.  TF2 should work a little better, but you have to lower the dxlevel.  The safe rule is that programs don't work in wine, and then you have the occasional miracle and it *kinda *works.  Its still great though.  Pretty okay for older games.

---

### Post by ODF on 2008-01-29
> **upbeat.linux said:**
> What version of wine are you running?

0.9.54

---

### Post by cthulhu666 on 2008-06-06
What did you expect?

Do you know how (especially the 3D parts of) Wine works?

Most win32 libraries are "just" Linux-native versions of windoze libraries with the same functionality. Direct3D however is quite a bit more complex, at there are no D3D drivers for X11/Linux. Thus all D3D calls have to be translated into corresponding OpenGL calls. This is in nature very complex and therefore (as stated above) almost a miracle that it works. In many cases (eg. WoW and LOTRO) it does work. It even works very well and sometimes even better that on windoze.

Kudos to the Wine developers who are doing an outstanding job!

BTW your Wine version is hopelessly old...

---

### Post by Sleaka J on 2008-06-06
> **cthulhu666 said:**
> 
BTW your Wine version is hopelessly old...

Yeah, but did you notice his post was the 30th January?

Sure, it's old today, but in January it was the latest version.

---

### Post by cthulhu666 on 2008-06-07
> **Sleaka J said:**
> Yeah, but did you notice his post was the 30th January?
LOL - nope, I didn't even notice that. I guess that explains it.

---

