---
title: "Wine won't install tahoma font!"
date: 2015-05-04
forum: Wine
---

### Post by julianpicart on 2015-05-04
No matter what I do, tahoma won't install. I tried using scripts, terminal, wine tricks and they all fail. Can you guys please assist me and help me install this font? Thank you so much!

---

### Post by Mark Phelps on 2015-05-05
Have you tried the instructions in the linked page: [http://wine-wiki.org/index.php/Fonts#Installing_Windows_Fonts]("http://wine-wiki.org/index.php/Fonts#Installing_Windows_Fonts")

---

### Post by julianpicart on 2015-05-05
I just tried it but get an error. 
I did [COLOR=#000000][FONT=monospace]wine tahoma32.exe /Q but got
[/FONT][/COLOR]wine: cannot find L"C:\\windows\\system32\\tahoma32.exe"
And now my font for terminal is all messed up! Text aren't displaying correctly

---

### Post by Mark Phelps on 2015-05-07
You have to do the "wget" line first -- in order to retrieve the font file.

Without that, there is no font file to use to install the font.

---

