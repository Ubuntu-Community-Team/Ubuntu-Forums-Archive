---
title: "Compiz message on start: Switching to using non-fbo path"
date: 2006-08-26
forum: x86 64-bit Users (Pre April '08)
---

### Post by chrilleh on 2006-08-26
I'm starting compiz by running the following script:
```

#/usr/bin/startcompiz.sh
#!/bin/sh

gnome-window-decorator --replace &
cgwd --replace &
compiz --replace gconf &
```

```

#/etc/gdm/gdm.conf-custom

0=Xgl

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl -fullscreen -br -accel xv:fbo -accel glx:pbuffer
flexible=true
```

Compiz runs just fine but when i start it with startcompiz.sh i get the following message in the terminal 

```
** (cgwd:5704): WARNING **: Cannot open pixmap: unshade

** (cgwd:5704): WARNING **: Cannot open pixmap: above

** (cgwd:5704): WARNING **: Cannot open pixmap: unabove

** (cgwd:5704): WARNING **: Cannot open pixmap: sticky

** (cgwd:5704): WARNING **: Cannot open pixmap: unsticky
Switching to using non-fbo path

```

The pixmap warnings is nothing to worry about, i think the theme I'm using is missing those. 
But is the "Switching to using non-fbo path" an error or just a warning. Should I do anything about it?

---

### Post by ericesque on 2006-09-01
beeeeeeee-ump! :)

any ideas anyone?

---

