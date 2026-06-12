---
title: "freezing when playing a dvd"
date: 2008-05-23
forum: x86 64-bit Users
---

### Post by dustynus on 2008-05-23
Hey,

This was happening on a previous install of 8.04:
Try to play a dvd, computer freezes up, except mouse and hotkeys (volume + brightness) still work, all buttons are just frozen.
Playing videos would do this too, on occasion, certain types of videos..couldn't narrow down exactly what kind would though.

Reinstalled 8.04,
installed libdvdread3 from
usr/share/doc/libdvdread3/install-css.sh
+ I installed vlc.

I try to open the disc in vlc, and boom, it freezes the computer again. Fresh reboot, doesn't fix anything.

Please help, thanks
:guitar:

---

### Post by gsmanners on 2008-05-23
Try going into Settings/Preferences, enable "Advanced options", then change the Video/Output modules setting to something like X11 or OpenGL. It could be that XVideo isn't working right for some reason.

---

### Post by dustynus on 2008-05-24
Sorry, where exactly is this? Are you talking about changing it for the individual movie player ? Or system wide ?

---

### Post by soxs on 2008-05-24
Happened to me once aswell, when I added a minivcd into my box, just blackscreen, had to hardreste.

---

### Post by gsmanners on 2008-05-24
> **dustynus said:**
> Sorry, where exactly is this? Are you talking about changing it for the individual movie player ? Or system wide ?

You said you installed VLC and tried it out in VLC and that you had problems when you ran VLC, so where do you think I'm referring to?

:lolflag:

---

### Post by philinux on 2008-05-24
Change from default.

---

### Post by dustynus on 2008-05-26
Thanks, I changed my gstreamer-properties to no Xv and it seemed to have fixed it.

Thanks :)

---

