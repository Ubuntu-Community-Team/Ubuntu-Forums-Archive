---
title: "HDD boot can't switch Virtual Terminals. Install CD Can"
date: 2007-10-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by kleinad on 2007-10-02
Control-Alt-F1 (Control-Alt-Fn where n = 1..6) does not work in the boot from harddisk, but it does on the boot from the install CD.

gettys are running.

sudo chvt 1 works.  Once in the VT, I can use the control-alt-fn keys to switch to the other VTs and back to X.  Once back in X, cannot switch to VTs with control-alt-fn.

Checked the Xkb settings in /etc/X11/xconf.org .  Tried a few different layouts/variants. Finally, matched my harddrive contents with the contents in this file during install CD boot.  Still does not work.  Was set to "macintosh" from the installer (running on Macbook Pro), now is set to "pc105" based on the installer's version.

Looking at xev output, can get "state 0xc, keycode 67 (keysym 0xffbe, F1)" to appear through the pressing of my keys.  Something seems to be keeping this combo from reaching whatever switching logic there is.

My last remaining guess is that maybe it is gdm's fault.  I haven't really pursued investigating this yet.  Would anyone here happen to know how to fix this?

Thanks for your time and help in advance,

Daniel

---

### Post by kleinad on 2007-10-02
Figured it out...  For anyone having the same problem, please try removing the XkbVariant line from /etc/X11/xorg.conf

The relevant section for me now looks like:


Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "macintosh"
EndSection

---

