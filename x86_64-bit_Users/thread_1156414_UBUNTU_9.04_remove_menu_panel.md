---
title: "UBUNTU 9.04 remove menu panel"
date: 2009-05-11
forum: x86 64-bit Users
---

### Post by pspmasterpro on 2009-05-11
Hello, I've recently installed the Awn dock for Ubuntu and now I want to remove the main menu panel at the top of the desktop. I've searched but those methods don't seam to work with 9.04 version of ubuntu. Can someone please post instructions on how to remove the Gnome menu panel completely. Thank you.

---

### Post by tuxxy on 2009-05-11
Have you tried to right click > delete panel

---

### Post by pspmasterpro on 2009-05-11
Yes I tried to right click > Delete panel but that option is grayed out.

---

### Post by lvleph on 2009-05-11
As far as I know you can remove all but one panel. You can use gconf-editor to set size to something small and it's hide size to 0.

---

### Post by JK3mp on 2009-05-11
+1 just set it to hide. :) , or use a light WM like Openbox or Fluxbox standalone with AWN if you don't wanna panel, it'd be better than getting the slack of gnome (though not that bad) without the panel and menu, etc.

---

### Post by pspmasterpro on 2009-05-11
O.K. using gconf-editor where do I go to set the hide size to 0, and is it possible to terminate this panel from starting up when Ubuntu boots up.

---

### Post by pixel :-) on 2009-05-11
a couple of minutes on google :)

> For versions of GNOME after version 2.22 (for example, Ubuntu Intrepid and later, or Fedora 10 and later), there are two options.

If you have "Configuration Editor" (AKA gconf-editor) installed, run it and navigate to the key folder /desktop/gnome/session. Double-click on the key required_components_list in the right-hand pane to edit it, and remove the value "panel" by selecting it and pressing the "Remove" button, followed by the "OK" button.

Alternatively, you can run the following command from the terminal:

gconftool-2 --type=list --list-type=string --set /desktop/gnome/session/required_components_list '[windowmanager,filemanager]'

[http://wiki.awn-project.org/FAQ#How_do_I_turn_Awn_into_a_launcher-only_dock.3F](http://wiki.awn-project.org/FAQ#How_do_I_turn_Awn_into_a_launcher-only_dock.3F)

And i supose you can uninstall it then.

---

