---
title: "GMD interface fails."
date: 2006-05-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by Porky on 2006-05-23
Me and some friends have installed ubuntu on this old G3 we got our hands on. It boots just fine, but the interface fails to load. Well, we do get the wallpaper, and the filebrowser accessible through a CDROM-icon, but that's it. We're wondering if there's any way to fix this problem without reinstalling.

---

### Post by ssam on 2006-05-23
sounds like gnome-panel is not loading.

can you try pressing CTRL+ALT+F1, and logging in to a terminal. then running
```
DISPLAY=:0 gnome-panel
```
in the terminal.

are there any error messages?

if you press CTRL+ALT+F7 to get back to gnome, do you see the panel?

---

### Post by Porky on 2006-05-23
Gnome-panel now loads (we did an apt-get gnome-panel install), seems it was deleted somehow. Anyway, we get error messages concerning "OAFIID:GNOME_MixerApplet" and "OAFIID:GNOME_Panel_TrashApplet". Do you by chance know how we get retrieve this applications? The error message asks to delete or let be, we're leaving them (for now) and doing a software-update.

---

