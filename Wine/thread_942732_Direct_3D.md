---
title: "Direct 3D"
date: 2008-10-09
forum: Wine
---

### Post by rasmus91 on 2008-10-09
Hi

just installed NWN2 in wine, as everything seemed to work, i tried to run the game, but no luck.

I got the message: "Could not find any 3D renderer card, this application will quit now" (i have a 3D rendering card, else i couldn't run this game i vista)

what do i do?

---

### Post by asdfoo on 2008-10-09
> **rasmus91 said:**
> Hi

just installed NWN2 in wine, as everything seemed to work, i tried to run the game, but no luck.

I got the message: "Could not find any 3D renderer card, this application will quit now" (i have a 3D rendering card, else i couldn't run this game i vista)

what do i do?

which video card, which drivers, which version of wine?

---

### Post by rasmus91 on 2008-10-10
the video card is Intel GMA 4500 MHD.

I have no idea what driver it is, didn't install anything my self.

I just installed the newest version of wine available through the "add/remove programs" (is it called synaptics package manager?)

---

### Post by Thelasko on 2008-10-10
Did you install DirectX in Wine?  You aren't supposed to, Wine forwards DirectX commands to OpenGL.  Installing DirectX breaks that.

---

### Post by rasmus91 on 2008-10-10
oops... damn, how to undo?

---

### Post by Thelasko on 2008-10-10
> **rasmus91 said:**
> oops... damn, how to undo?

The fastest way is to uninstall Wine and delete the .wine file in your /home folder. (it's hidden, press ctrl+h to show it)  Reinstall wine and run Winecfg (i.e. "wine configuration," it recreates the .wine folder when you first start it).

Hopefully you don't have a lot of programs installed in Wine because they will be deleted too.  There might be another way to fix it but, I don't know what it is.

---

### Post by Thelasko on 2008-10-10
The author of [this page]("http://ubuntuforums.org/showthread.php?t=497332") says that it's out of date, but I still think it's useful.  Have a look through it.  It's a good resource if you run into trouble.

---

