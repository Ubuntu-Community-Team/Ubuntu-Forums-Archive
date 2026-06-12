---
title: "Gnome/Freetype/Cairo Freaking Out!"
date: 2007-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by cdizzle on 2007-06-06
So I was trying to install a piece of software, CompuCell3D, from source for some research I was doing and I needed to install a bunch of new packages. CompuCell3D was the only piece of software I installed by source, all of the other stuff I did with aptitude. I do know that at one point libfreetype6 was downgraded or something. 

Now nothing in gnome works, not even gdm. They will try to load and fail every time. I then installed KDE which works fine, and now upon trying to load any gnome app, or pretty much anything I had installed before like synaptic, I get the following message:
```
synaptic: symbol lookup error: /usr/lib/libcairo.so.2: 
undefined symbol: FT_Library_SetLcdFilter
```

But if i'm root and I try to run synaptic (or any of the other apps) I get:

```
root@metalaptop-linux:/home/cdizzle# synaptic
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(synaptic:16871): Gtk-WARNING **: cannot open display:
```

I'm running these commands in konsole, I've reinstalled gdm and ubuntu-desktop, but not all their dependencies. Additionally, aptitude without any args tells me a whole bunch of my packages are "broken" and need to be uninstalled and my kernel downgraded. What gives?

---

### Post by Kilz on 2007-06-06
Sounds like a first class fubar!  :D

---

### Post by cdizzle on 2007-06-07
So when I installed feisty, I followed the instructions in this thread without thinking about them much: [http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670)

The libxft and libfreetype were downgraded when I was installing CC3D, but not libcairo2. When I downgraded libcairo2 to main, everything worked.

---

