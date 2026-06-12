---
title: "Gnome-Sudoku Problem"
date: 2006-12-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Permafrost91 on 2006-12-25
RESOLVED! (see below)

[COLOR="Gray"]I just installed gnome-sudoku via Synaptic under Dapper 64bit and when I run it from the command line I get this output:

```
Traceback (most recent call last):
  File "/usr/games/gnome-sudoku", line 10, in ?
    from gnome_sudoku.gnome_sudoku import start_game
  File "/usr/lib/python2.4/site-packages/gnome_sudoku/gnome_sudoku.py", line 18, in ?
    pb = gtk.gdk.pixbuf_new_from_file(os.path.join(IMAGE_DIR,filename))
gobject.GError: Couldn't recognize the image file format for file '/usr/share/gnome-sudoku/Footprints.svg'
```

any ideas on what the problem here might be? Thanks![/COLOR]

---

### Post by Permafrost91 on 2006-12-25
I solved the problem by compiling the latest version (0.7.1) from the homepage from source. Works like a charm now!

---

