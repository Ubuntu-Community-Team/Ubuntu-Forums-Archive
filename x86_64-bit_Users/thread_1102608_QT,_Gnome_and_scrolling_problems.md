---
title: "QT, Gnome and scrolling problems"
date: 2009-03-21
forum: x86 64-bit Users
---

### Post by sjbaugh on 2009-03-21
I am using Ubuntu 64 bit Intrepid.

When I am using Gnome as my desktop I am finding that when I use ERIC for Python development of my QT4 program I get scrolling problems in the edit window and in a scrolling window in the program I am developing. When I click on a point in the edit window the window scrolls to a different place and I end up clicking on something I wasn't trying to click. Scrolling up leaves some text in the wrong place, making it difficult to read. I get a similar problem with the scrolling graphics window in my application. The application still exhibits this problem if I run it from DrPython.

On the same machine I have Fedora 32 bit and I have also tried KDE on my 64 bit installation and I do not get any problem. With 64 bit Gnome it is also OK if I disable compiz.

I also have Ubuntu 32 bit on a different machine and do not get this problem.

The problem seems to be with 64 bit Gnome/compiz.

I have an nVidia graphics card and have tried both the 177 and 180 version drivers.

Anybody got any ideas?

Steve, England

---

### Post by peutch on 2009-08-11
Hi!

I have exactly the same problem when using Kile and Okular under Gnome. Scrolling and display is completely messed up, with some part of the screen updating only when I hover over them with the mouse.

The problem also affects the menus, as shown in Kile, see attachment for a screen capture. Some of the buttons belongs to the previously displayed menu, while some belong to the menu actually displayed. There is some overlap.

I'm running ubuntu Jaunty with nvidia driver 180.

The problem does NOT occur when I launch: kile --graphicssystem raster

So it seems like it is something related to the graphic system of Qt...

I'll look for Launchpad bug on this.

---

### Post by michmike on 2009-09-24
Same problem. Kile and Okular do not render properly under Gnome. Any news?

---

