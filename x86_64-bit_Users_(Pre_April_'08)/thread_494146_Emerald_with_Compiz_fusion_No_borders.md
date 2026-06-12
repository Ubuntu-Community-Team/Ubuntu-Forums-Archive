---
title: "Emerald with Compiz fusion: No borders"
date: 2007-07-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by shafin on 2007-07-06
After I activated emerald under Compiz fusion,window borders went invisible,I can still click those "invisible" buttons.What should I do?

---

### Post by dmfield on 2007-07-10
if you get this working, let me know. I don't get any borders...

---

### Post by Case_f on 2007-07-10
Just checking, is your Emerald up-to-date?

---

### Post by dmfield on 2007-07-10
Assume so... i'm not that bothered to be honest, its pretty, but i can live without it for now..

---

### Post by shafin on 2007-07-10
Emerald is not working anyway,so please name some good gnome themes for use

---

### Post by Ocxic on 2007-07-10
try running "compiz --replace -c emerald" twice, with alt-f2. works for me

---

### Post by Sayers on 2007-07-19
To the above post:

Wow, that worked great! Thank you very much.

---

### Post by dmfield on 2007-07-19
I also found that you have to remove Compiz from Feisty. (I did this from Synaptics and searched for Compiz) this has to be done BEFORE you install compiz fustion, or it won't work on the x86_64bit version at least.

---

### Post by bborror on 2007-07-20
[QUOTE="dmfield"]I also found that you have to remove Compiz from Feisty. (I did this from Synaptics and searched for Compiz) this has to be done BEFORE you install compiz fustion, or it won't work on the x86_64bit version at least.[/QUOTE]

Learned that one the hard way today. #-o I used aptitude to remove all/fix/upgrade(final working solution was nuts) then did a --reinstall from tr3vin0's repo just to be safe :P

Adding some emerald goodness now :mrgreen:

---

### Post by shafin on 2007-07-28
Problem solved.:D

This problem was caused by incompatible versions of Compiz Fusion and Emerald.Emerald was version 0.2.1,which was for Beryl only.So I installed version 0.3.0 which is for both emerald and beryl.

However,I had to completely remove and reinstall compiz to get this to work.And one more small problem.Now I cant get the metacity themes to work with compiz.They worked fine previously.

Thanks to everyone who helped.Thanks a lot.

---

### Post by rhonaldmoses on 2007-07-30
Hi,

Compiz-Fusion was working perfectly until I updated the compiz through automatic updater. After updating, when I try to enable desktop effects, I got dekstop effects without borders. I tried following the following link ( [http://linuxevangelist.blogspot.com/2007/06/ubuntu-7-no-window-borders-on-desktop.html](http://linuxevangelist.blogspot.com/2007/06/ubuntu-7-no-window-borders-on-desktop.html) ) which worked like a charm under openSuSE when I had the same issue, but under Ubuntu 7, I lost my GUI completely, however, I reverted the changes back and got back into the GUI, now how do I rescue my old compiz-fusion without re-installing ubuntu?


Also, despite updating Compiz-Fusion with automatic updater so many times, it still gives me notification that there is update found for the Compiz-fusion packages I installed already.

Can someone show some light into my life?

Thanks in advance.

---

