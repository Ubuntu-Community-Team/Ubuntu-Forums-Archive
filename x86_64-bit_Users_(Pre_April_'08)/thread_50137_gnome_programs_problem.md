---
title: "gnome programs problem"
date: 2005-07-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tamir on 2005-07-19
Hi all,
I have a problem with many based gtk+ programs.
like gedit or file roller, when I start file-roller on console it gives me:
```
/home/tamir/.themes/Crystal dlb/gtk-2.0/gtkrc:9: Unable to find include file: "panel.rc"
/home/tamir/.themes/Crystal dlb/gtk-2.0/gtkrc:10: Unable to find include file: "toolbar.rc"
/home/tamir/.themes/Crystal dlb/gtk-2.0/gtkrc:481: Unable to locate image file in pixmap_path: "gfx/menuline.png"
/home/tamir/.themes/Crystal dlb/gtk-2.0/gtkrc:484: Background image options specified without filename
/home/tamir/.themes/Crystal dlb/gtk-2.0/gtkrc:910: Unable to locate image file in pixmap_path: "gfx/scrollbar_horizontal_insens.png"
/home/tamir/.themes/Crystal dlb/gtk-2.0/gtkrc:914: Background image options specified without filename
/home/tamir/.themes/Crystal dlb/gtk-2.0/gtkrc:939: Unable to locate image file in pixmap_path: "gfx/scrollbar_vertical_insens.png"
/home/tamir/.themes/Crystal dlb/gtk-2.0/gtkrc:943: Background image options specified without filename
``` 
and only after something like **10-15 Minutes** the programe shows.
when I change to another theme, I dont have all of this output, but I have too wait 10 minutes too.

does someone have this problem too?

---

### Post by negatory on 2005-07-19
Weird, I was going to say that you've got a broken theme but you say that you also have to wait with another themes....even with the default one?
I'm not experiencing any of these...but I'm using the default theme and never changed it...
Pedro Carrico

---

### Post by Tamir on 2005-07-19
[QUOTE=negatory]Weird, I was going to say that you've got a broken theme but you say that you also have to wait with another themes....even with the default one?
I'm not experiencing any of these...but I'm using the default theme and never changed it...
Pedro Carrico[/QUOTE]
 oh, I just don't want to reinstall hoary, with all the packages i have..

---

### Post by DancingSun on 2005-07-19
Hmmm....my "/home/username/.theme/" directory is empty...maybe some environment variables were changed so it's pointing at the wrong place?

Or maybe you installed additional themes.  Try the themes that come with Ubuntu and see if they work correctly.

---

### Post by Tamir on 2005-07-19
I tried with Human theme, the same, just without output :\
I decided to reinstall Ubuntu Hoary.

---

