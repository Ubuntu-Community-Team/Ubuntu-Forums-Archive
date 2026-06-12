---
title: "No fonts in Wine to run windows program, copying over?"
date: 2008-06-17
forum: Wine
---

### Post by calicat on 2008-06-17
The fonts folder is blank in the wine directory and I cant run PS7 without the windows default fonts.  I have tried copying them from the main directory over, but when I do they go to install icon and a lock.  I have found the other truetype fonts that I need on the internet to download, but how do I get them into .wine and get them to work?  I do not have access to a computer with windows on it to just copy their directory and I am going to have to some way get them off the net and into the right direcotry.  

I should mention that I am pretty new to Ubuntu and though I love the way my computer performances, it is frustrating to learn, lol, so any instructions should be in simple terms please :KS

---

### Post by cogadh on 2008-06-17
The fonts folder in the .wine directory should be empty, its only really there if an application needs to install its own font. Wine actually uses the Ubuntu system fonts. If you have an app that needs Microsoft fonts, then install the MS core fonts package:
```
sudo apt-get install msttcorefonts
```

---

### Post by calicat on 2008-06-17
> **cogadh said:**
> The fonts folder in the .wine directory should be empty, its only really there if an application needs to install its own font. Wine actually uses the Ubuntu system fonts. If you have an app that needs Microsoft fonts, then install the MS core fonts package:
```
sudo apt-get install msttcorefonts
```

I've done that, but I'm still getting the error message that there is no default font found when I run PS7 and I can't enter any text.  I can do everything else in PS, but no text.

---

### Post by Roryking on 2008-06-18
Your fonts folder is:

~./wine/windows/fonts

---

### Post by cogadh on 2008-06-19
After a little research, this is a known bug:
[http://bugs.winehq.org/show_bug.cgi?id=9623](http://bugs.winehq.org/show_bug.cgi?id=9623)
It supposedly can be resolved by using [winetricks](http://wiki.winehq.org/winetricks) to install the core fonts into Wine.

---

### Post by calicat on 2008-06-19
> **cogadh said:**
> After a little research, this is a known bug:
[http://bugs.winehq.org/show_bug.cgi?id=9623](http://bugs.winehq.org/show_bug.cgi?id=9623)
It supposedly can be resolved by using [winetricks](http://wiki.winehq.org/winetricks) to install the core fonts into Wine.

THANK YOU!  It worked and I can now type in PS7!!!!!  :guitar: You ROCK! :guitar:

---

