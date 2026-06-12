---
title: "Steam and no text!  Anyone manage to fix this?"
date: 2005-07-04
forum: Wine
---

### Post by dezgot on 2005-07-04
I managed to get wine 20050111 set up properly i think, and i got steam installed, but when i run it, there is absolutely no text in the Steam windows.  The buttons and all seem to work and I can blindly login, but beyond that i have no clue what's going on.  I have tried putting the Tahoma and Marlett every which place with no luck.  

Anyone have this happen and fix it one way or another?

---

### Post by claydoh on 2005-07-04
Valve worked with Transgaming to get [Steam/Half-life 2/etc to run using Cedega,]("http://digital-conquest.ath.cx/wiki/index.php/Half_Life_2") and there is [a special Mozilla activex control that needs to be installed]("http://digital-conquest.ath.cx/wiki/index.php/Cedega-4.2#New_Mozilla_Control")[ ]("http://a%20special%20Mozilla%20activex%20control%20that%20needs%20to%20be%20installed%20")in order to get cedega to show text. I am not sure if anyone has gotten steam to run in "normal" wine just yet, but it works wonderfully for me using Cedega.

---

### Post by Xoomer-Linux on 2007-07-22
I got the same problem, but cedega is NOT FREE!.. Can't we fix this problem alone?

(sorry i bumped one year old thread but it's annouing that cedega is not free.. i don't use any credit card, but i still need to use steam.. and i bought the steam games on an official Game of the year edition DVD)

---

### Post by BlahMan_of.Doom on 2007-07-22
Put tahoma.ttf in ~/.wine/drive_c/windows/fonts

---

### Post by Xoomer-Linux on 2007-07-22
yes, sey i know i just saw it on the valve developer community
>     Steam uses the font Tahoma which is included in all Windows versions, but is not available on Linux. This will result in invisible text when running Steam without installing Tahoma first. 
    The easiest way to work around this issue is to put a copy of tahoma.ttf from a Windows installation (%WINDIR%\Fonts) to ~/.wine/drive_c/windows/fonts.

---

### Post by jacob01 on 2007-07-22
or you could down lod the font just search it. also i ran into a problem were i didnt have a plugin installed and could not see the market place what prob are you getting

---

### Post by jacob01 on 2007-07-22
i had the same problem i got a the font but it didnt work so i downloaded another and restarted the install and it worked

---

### Post by FunkDip on 2008-03-26
I had [SIZE="5"]immediate success[/SIZE] when I copied tahoma.ttf to [FONT="Fixedsys"]/usr/share/wine/fonts[/FONT] and restarted Steam through PlayOnLinux.

---

