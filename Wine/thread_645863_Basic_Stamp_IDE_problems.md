---
title: "Basic Stamp IDE problems"
date: 2007-12-20
forum: Wine
---

### Post by kf4mat on 2007-12-20
I seem to be lost; as much as I try I don't seem to be getting anywhere in trying to get Parallax's Basic Stamp IDE to function using wine.  I really need this program running on my laptop and since I can't get it to work was wondering if anyone here has had any luck.

---

### Post by cogadh on 2007-12-20
According to Wine's Application Database, it does work, but there hasn't been any recent testing and there is a reported problem with one version of the app, but no workaround provided:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=4451](http://appdb.winehq.org/objectManager.php?sClass=application&iId=4451)

---

### Post by kf4mat on 2007-12-20
Hey,

Not sure where the rest of my post went, I had another paragraph that detailed what steps I had gone through.

I concur with your reply but.... Before making my initial post I had gone to the wine page and looked through the apps database and saw the two entries for this software. The problem is they are both testing versions which aren't available as downloads anymore.

The current version opens under wine and even goes through the install wizard, it just doesn't install anything that runs. When I look the wine folder under the Application menu it shows nothing.

Tm

---

### Post by barney_1 on 2008-01-17
You need to navigate to the installed folder and launch it yourself:
```
~/.wine/drive_c/Program Files/Parallax Inc/Stamp Editor v2.2.6
```

then run it with:
```
wine Stampw.exe
```

The problem I'm having is it doesn't see my Basic Stamp 2e.

---

