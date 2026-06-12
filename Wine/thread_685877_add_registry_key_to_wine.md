---
title: "add registry key to wine"
date: 2008-02-02
forum: Wine
---

### Post by Mr.Johnny on 2008-02-02
Hi!

How do I add registry keys to wine?

I want to use a plugin I bought in it, I click on my registration key, a popup box shows "Success" but when I run it still says unregistred.

is there any "regedit" equivalent for wine?

thanks.

---

### Post by luisromangz on 2008-02-02
Try "wine regedit". It should do the trick.

---

### Post by happyhamster on 2008-02-02
> **Mr.Johnny said:**
> 
is there any "regedit" equivalent for wine?

Yep, it's called "regedit" :)

An easy way of using it is by making a small text file with the key(s) you want to import. For example (one I use frequently):

[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"DirectDrawRenderer"="opengl"
"VideoMemorySize"="256"
"UseGLSL"="enabled"
"OffscreenRenderingMode"="fbo"
"RenderTargetLockMode"="auto

And then import it using:

wine regedit name-of-file.reg

or just 

regedit name-of-file.reg

---

### Post by diaa on 2008-02-02
what about
```
wine ~/.wine/drive_c/windows/regedit.exe
```

It's strange to be stored in your home directory but it works anyway :)

---

### Post by Mr.Johnny on 2008-02-02
hey, I just typed regedit in the terminal and bang... there it was. :lolflag: thanks

---

### Post by Toffeeapple on 2008-02-03
If you have installed anything with it's own wine directories.... for example...

 WINEPREFIX="$HOME/Games/Guildwars" wine regedit

that would edit the registry for my installation of Guildwars.

this is where i found out how to do it : )
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3696](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3696)

---

