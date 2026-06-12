---
title: "Which comctl32.dll?"
date: 2008-01-10
forum: Wine
---

### Post by atarileaf on 2008-01-10
I'm trying to run a Bible study program called Watchtower Library under wine and one of the instructions is to get a copy of comctl32.dll from an XP computer. When I did a search of my XP Home machine I found several copies of this file under different directories in Windows, including one in the system32 folder. Each of these comctl32.dll's is also different sizes. 

I'm supposed to insert and overwrite this .dll into the system32 folder in wine. Should I use the one from the system32 folder of my XP machine because the instructions aren't clear. There is no mention of the possibility of multiple comctl32.dll's to choose from so I just want to make sure I use the right one.

The instructions are here that I'm using:
[http://wiki.jswindle.com/index.php/Watchtower_Reader_2006#ubuntu_6.06_-_7.10](http://wiki.jswindle.com/index.php/Watchtower_Reader_2006#ubuntu_6.06_-_7.10)

Thanks

---

### Post by FriedChips on 2008-01-10
Yes use the one from the system32 folder, any multiple copies are probably the same anyway. Windows keeps multiple copies of many .dll files but they basically backups.. If you really want to know if they are the same you can use kdiff or just compare file sizes, but try the one from the system32 folder first.

---

### Post by atarileaf on 2008-01-10
Thats what I thought but I wanted to be sure.
Thanks

---

