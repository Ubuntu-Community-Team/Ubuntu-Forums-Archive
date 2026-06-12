---
title: "Installed program is missing"
date: 2008-05-19
forum: x86 64-bit Users
---

### Post by knife_party on 2008-05-19
hi there everyone. I've got a problem. Lately i've been installinf amny programs using the synaptic packages manager. But strangely enough, i couldn't find some installed programs, such as aRts, bristol, and cheesetracker. I know these are audio programs, but i don't see them in the applications/audio drop down menu. I've searched the /usr folder, i do found the applications data such as the bmp, but still i cannot find the executable file. Can anyone help me? Many thanks in advance.

---

### Post by jocko on 2008-05-19
> **knife_party said:**
> hi there everyone. I've got a problem. Lately i've been installinf amny programs using the synaptic packages manager. But strangely enough, i couldn't find some installed programs, such as aRts, bristol, and cheesetracker. I know these are audio programs, but i don't see them in the applications/audio drop down menu. I've searched the /usr folder, i do found the applications data such as the bmp, but still i cannot find the executable file. Can anyone help me? Many thanks in advance.

aRts is a sound server for kde, pretty much like pulseaudio or esound is/was in ubuntu (gnome).
I'm not sure why you would like to run it in ubuntu, as it's probably not very well integrated into gnome, but you probably have to add it to the session (System --> Settings --> Sessions) or start it from a terminal (and probably disable pulseaudio as well, as I don't see why you would want to run two sound servers at once).
The two others I have no idea what they are, but you can probably run them from a terminal or make your own starters.

---

### Post by knife_party on 2008-05-20
umm..how can i make my own starters?

---

### Post by jocko on 2008-05-21
> **knife_party said:**
> umm..how can i make my own starters?

Right click the desktop and pick "create starter" from the menu.
As startup command, use the filename of the actual executable file (usually the same as the name of the application, try typing it in a terminal first. if it works in a terminal it will work from a starter).

To add it as a menu item, just right click the menubar on the panel and select "edit menus" to start alacarte (the gnome menu editor). In alacarte, select the submenu you want to add it to (i.e program --> Audio & Video) and click the "new item" button to create a new starter.

---

