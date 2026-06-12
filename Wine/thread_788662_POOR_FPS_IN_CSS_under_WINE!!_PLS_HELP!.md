---
title: "POOR FPS IN CSS under WINE!! PLS HELP!"
date: 2008-05-09
forum: Wine
---

### Post by dtrot55 on 2008-05-09
I installed Ubuntu because I wanted to try it out and also heard in some cases that the game ran better than windows...well i got steam installed and get into a game just fine..but...I GET LIKE 9-20 FPS....I have a Nvidia 8600 GT ... yeah its not the best but its way better than this game can show and works flawlessly on Windows....anyone know what is going on...if i cant play the game on Ubuntu then I will have to resort to windows and im trying to find a means to get away from it.

System:
Amd64 x2 4200+
1.5g DDR1 3200 Ram
Biostar T-Force 6100-939
Nvidia 8600 GTXXX 256mb PCIe

Thanks!

---

### Post by schtufbox on 2008-05-10
try entering this in a terminal before playing CS: S

metacity --replace &

This will switch off compiz and perhaps improve your fps, though, seeing as I have a lower end card ( 7300GT) and get more FPS while leaving compiz on, I am not sure it will help..but worth a try :)

After you finish playing you can do 

compiz --replace &

to switch compiz back on

---

### Post by dtrot55 on 2008-05-10
tried that....didnt work ... still only getting 20 max FPS

---

### Post by Ky3r0z on 2008-05-10
> **dtrot55 said:**
> tried that....didnt work ... still only getting 20 max FPS

Try setting the textures and everything to low. Try the fixes found here [http://gaming.gwos.org/doku.php/wine:winestuff](http://gaming.gwos.org/doku.php/wine:winestuff)

---

### Post by dtrot55 on 2008-05-11
Reformatted to 8.04 x32 and enabled nvidia drivers and WINE is still getting low FPS....any idea?

---

### Post by 0ni on 2008-05-11
Downloaderize these drivers:
[http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html)

---

