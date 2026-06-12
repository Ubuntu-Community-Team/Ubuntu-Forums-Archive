---
title: "How to safely uninstall .wine ??"
date: 2012-02-24
forum: Wine
---

### Post by dragonfly41 on 2012-02-24
I am about to uninstall wine from Ubuntu 10.10 and all wine installed programs.

I've uninstalled wine programs .. but I would like to purge all wine related folders.

the brute force approach appears to be to delete [COLOR=Navy]/home/myusername/.wine[/COLOR]

but in this folder I see a subfolder [COLOR=Navy]dosdevice[/COLOR]s which contains subfolders ..

c: and z:

It is the z: subfolder which puzzles me since this contains ubuntu like folders:

bin
boot
boot-sav
build
cdrom
...
sys
tmp
usr 
etc. etc.

First question is what is this z: folder which is a duplicate of the ubuntu root folder?

Next question is if I delete the .wine folder it would appear to delete z: (and possibly ubuntu content).

So what is the safest way of uninstalling and purging wine?

---

### Post by iponeverything on 2012-02-24
```
dpkg -r --purge wine
```

---

### Post by ohadcn on 2012-02-24
you can remove it
if you look carefully you find that the z folder is a link to your ubuntu root folder and it is there just to allow programs running under wine to access your files

---

### Post by howefield on 2012-02-24
Thread moved to the "*Wine*" forum.

---

### Post by Soulcage on 2012-02-25
[http://wiki.winehq.org/FAQ#head-ddc6f242056eb1a4fe566c9434d15fd8b64606aa]("http://wiki.winehq.org/FAQ#head-ddc6f242056eb1a4fe566c9434d15fd8b64606aa")

---

