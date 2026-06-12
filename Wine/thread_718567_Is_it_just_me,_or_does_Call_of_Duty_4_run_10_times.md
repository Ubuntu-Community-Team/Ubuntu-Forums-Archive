---
title: "Is it just me, or does Call of Duty 4 run 10 times better in the latest Wine?"
date: 2008-03-08
forum: Wine
---

### Post by piratesmack on 2008-03-08
I made a deb for the new wine (0.9.57) as soon as the source was released yesterday:
[http://files.filefront.com/wine+0957+1+i386deb/;9774956;/fileinfo.html](http://files.filefront.com/wine+0957+1+i386deb/;9774956;/fileinfo.html)

Maybe it's all in my head, but games like Call of Duty 4 seem to run much better. (Oh yeah, the Wine deb above has the alpha glow patch needed for COD4)

Enjoy

---

### Post by gloscherrybomb on 2008-03-09
Is there a 64 bit version?

---

### Post by Chriis on 2008-03-09
Same question, 64 bits version exist?

---

### Post by piratesmack on 2008-03-09
you should be able to run it on 64 by forcing the architecture:

-save the .deb package to your Desktop
-open a terminal
-Run this command
cd Desktop
(press enter)
sudo dpkg --force-architecture -i wine_0.9.57-1_i386.deb

---

