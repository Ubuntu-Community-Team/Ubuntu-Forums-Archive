---
title: "wine-doors image error"
date: 2008-03-01
forum: Wine
---

### Post by SuperBo on 2008-03-01
When I run Wine-doors, I have an error.
```
Traceback (most recent call last):
  File "/usr/share/wine-doors/src/ui.py", line 515, in on_render
    cell_area,opacity )#, animation )
  File "/usr/share/wine-doors/src/ctile.py", line 63, in __init__
    self.DrawTile()
  File "/usr/share/wine-doors/src/ctile.py", line 181, in DrawTile
    self.DrawRating()
  File "/usr/share/wine-doors/src/ctile.py", line 296, in DrawRating
    image = cairo.ImageSurface.create_from_png ( self.star )
cairo.Error: file not found
```
Please show me how to fix this error. Thank you.:lolflag::lolflag:

---

### Post by jeffus_il on 2008-03-01
Check to see if you have the python-cairo package installed, if not install it.

Mmm, after some fishing around, it seems like the self.star png file is missing and I found a diff on the internet at:
[http://www.wine-doors.org/trac/changeset/549?format=diff&new=549](http://www.wine-doors.org/trac/changeset/549?format=diff&new=549)
which removes this line, I would try to get a fixed version of the software.

---

### Post by SuperBo on 2008-03-01
How can I apply this diff file. I'm a newbie.

---

### Post by jeffus_il on 2008-03-01
First look for a later version, I'm not expert enough to guide you through that, need some time ...

---

### Post by SuperBo on 2008-03-01
I install wine-doors 0.1.2.  But the problem still happen.

---

