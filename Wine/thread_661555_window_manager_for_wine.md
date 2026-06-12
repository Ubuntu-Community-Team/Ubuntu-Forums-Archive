---
title: "window manager for wine"
date: 2008-01-08
forum: Wine
---

### Post by weeniewhite on 2008-01-08
I've tried running ReactOS explorer.exe under wine and I got a windows like desktop with a windows like taskbar, etc, but I had no window manager. I started metacity and then I started playing a bit with it. It didn't take me long to notice that metacity and explorer.exe are not good together. I also tried litestep and I got the same results.

In fact, I just feel like playing with wine as if I was under windows. Does anyone know a window manager for windows?

---

### Post by Faud on 2008-01-08
Ok, #1 and #2 are totally MY opion and you are free to do whatever you like. Just my 2 cents.

# 1 ReactOS is still in alpha stage and so unless you are gonna help develop it, why even mess with it ?

#2 No, no I dont. Sorry :lolflag:

---

### Post by weeniewhite on 2008-01-08
I'm just trying its explorer.exe.

---

### Post by hikaricore on 2008-01-08
The ***dows shell is a complicated mess of files and libraries aside from just explorer.exe.

You're not going to have much luck running it as a shell/window manager under WINE.
I've personally managed to run LiteStep on a virtual desktop to some degree, but much of the functionality was limited.

---

### Post by weeniewhite on 2008-01-08
I managed to run litestep under wine but I had no window borders.

---

### Post by hikaricore on 2008-01-08
Wine should provide its own window management even while running a program such as litestep on a virtual WINE desktop.  I can't image why it wouldn't.

Have you unchecked "Allow the window manager to control the windows." option in **winecfg**?

---

### Post by weeniewhite on 2008-01-08
Thanks. It worked when I unchecked Allow the window manager to control the windows.

I had a semi-usable desktop and a semi-usable window manager.

I'll try a couple of other shells until I get sick of it because nothing seems to work correctly.

Babye

---

