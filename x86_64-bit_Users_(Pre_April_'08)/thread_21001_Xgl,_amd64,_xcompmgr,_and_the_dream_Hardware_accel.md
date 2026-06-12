---
title: "Xgl, amd64, xcompmgr, and the dream Hardware accelerared shadows on ATi"
date: 2005-03-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by blinksilver on 2005-03-19
I am an ATi user and proud of it, well sorta,

the point is that i wanted shadows for my ATi laptop, so i went on a trip trying to figure out how, and came to this

the Ati x86_64 8.10.19 drivers
the latest CVS of Xgl
X.org 6.8.2
quartz 
a little fiddling
some serious googling and finally

I natively(64bit) compiled Xgl server on top of the ati drivers and X.org

i am now down to the last step, the automation process

this is how i turn it on,

Xglx :1 -ac -screen 1280x800 -fullscreen

but how do i get it it start with gnome, i found somewhere that said put 

Xglx:1 - ac - screen 1280x800- fullscreen & DISPLAY=:1 xcompmgr - c - f & DISPLAY=:1 /etc/X11/Sessions/Gnome 

into my xintrc, i but after looking at the xintrc, i think it is wrong, because (correct me if i am wrong) ubuntu does it a bit differently, any ideas

i am so close, please help

---

### Post by daniels on 2005-03-19
If you put that in .xinitrc, make it executable, and then select 'User session' or something instead of GNOME in gdm, everything should work fine.

---

### Post by blinksilver on 2005-03-20
thanks daniels, sadly, gnome will not start, it says that X returned an invalid value and refuses start

---

### Post by revellion on 2005-05-31
[QUOTE=blinksilver]I am an ATi user and proud of it, well sorta,

the point is that i wanted shadows for my ATi laptop, so i went on a trip trying to figure out how, and came to this

the Ati x86_64 8.10.19 drivers
the latest CVS of Xgl
X.org 6.8.2
quartz 
a little fiddling
some serious googling and finally

I natively(64bit) compiled Xgl server on top of the ati drivers and X.org

i am now down to the last step, the automation process

this is how i turn it on,

Xglx :1 -ac -screen 1280x800 -fullscreen

but how do i get it it start with gnome, i found somewhere that said put 

Xglx:1 - ac - screen 1280x800- fullscreen & DISPLAY=:1 xcompmgr - c - f & DISPLAY=:1 /etc/X11/Sessions/Gnome 

into my xintrc, i but after looking at the xintrc, i think it is wrong, because (correct me if i am wrong) ubuntu does it a bit differently, any ideas

i am so close, please help[/QUOTE]
 i would say .xsession

i usually symlink it from my .xinitrc so i can choose the default session in GDM/XDM that way

$ ln -s ~/.xinitrc ~/.xsession

Edit:

Tried with anything else other than Gnome?

---

### Post by Johan on 2005-06-05
I've been trying to get Xgl working on my computer with a nvidia card. It (finally :-) compiled but when I run it I get this:
```

johan@min:~ $ /opt/fdo/bin/Xglx :1 -ac -fullscreen
Initialized 1600x1200 back buffer offscreen area
Initialized 2048x2048 pbuffer offscreen area
Initialized 2048x2048 pbuffer offscreen area
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  27 (X_UngrabPointer)
  Serial number of failed request:  87
  Current serial number in output stream:  120

```

Relevant info in this case is probably that it's a 32-bit machine (K7).

I'm running a fully updated Hoary installation with the nvidia binary drivers. What can I do to make it work?

---

### Post by zAo on 2006-01-20
I'm also wondering how I can get Xglx to start at default. Anyone on this?

---

### Post by zasf on 2006-01-31
I'm very interested too, this is the best I can get from google [http://www.sebastian-bergmann.de/blog/archives/558-Xgl.html](http://www.sebastian-bergmann.de/blog/archives/558-Xgl.html), but still I'm not able to do it in ubuntu. 

I do
```
rm X && ln -s Xgl X
```

but still it loads normal Xorg at startup.. anyone could fit Bergmann's howto for ubuntu?

---

