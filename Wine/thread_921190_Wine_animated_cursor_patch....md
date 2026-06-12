---
title: "Wine animated cursor patch..."
date: 2008-09-16
forum: Wine
---

### Post by bhart007 on 2008-09-16
So does anyone know how to apply a patch to wine?  This is what I'm referring to: [http://bugs.winehq.org/show_bug.cgi?id=10708](http://bugs.winehq.org/show_bug.cgi?id=10708) Look down in the attachments section.

Evidently this ani patches are for games like C&C generals and the like that use animated cursors.  Without the patch you pretty much dont see a mouse cursor at all.

Thanks

---

### Post by nwlinkvxd on 2008-09-16
```

sudo apt-get build-dep wine
git clone git://source.winehq.org/git/wine.git ~/wine-git
cd ~/wine-git
patch -p1 < *******whatever the downloaded patch location is*******
./configure
make
sudo make install
```

Be sure to uninstall your existing copy of Wine first.


OH, one other thing: those patches look like they're for Wine 1.1.3 and earlier. If that's the case, you just need to download the latest Wine deb from [http://winehq.org/?announce=1.1.4](http://winehq.org/?announce=1.1.4)

---

### Post by bhart007 on 2008-09-16
wow, thanks for the help.

---

### Post by desertboy on 2008-09-16
[http://oliverdeisenroth.de/index.php?option=com_remository&Itemid=85&func=select&id=20](http://oliverdeisenroth.de/index.php?option=com_remository&Itemid=85&func=select&id=20)

has debs with the patch installed, he's the maintainer for C&C3:TW (Which needs it also) at appdb so I think his debs should be fine, I've never had any problems with them.

---

### Post by Toxicity999 on 2008-09-16
You don't need to uninstall your current copy of wine, in fact I would not recommend it... for compatibilities sake. It might or might not break other things (if it didn't, or was a clean patch, it would be i nthe wine tree by now)
 
./configure --prefix=/usr/local
 
this will install it to a place that will not overwrite current wine data. Such a minor modification should play fine with the same wineprefix (~/.wine).

---

### Post by jasex on 2008-09-19
Do either of you perhaps know of a 64-bit package like this. Strictly because it won't let me compile wine even after sudo apt-get build-dep wine

Not too sure exactly how to tell if the patch got applied.

---

