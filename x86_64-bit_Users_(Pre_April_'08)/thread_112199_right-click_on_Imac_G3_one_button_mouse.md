---
title: "right-click on Imac G3 one button mouse"
date: 2006-01-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by IdleOne on 2006-01-03
can anybody tell me how I right click with a mac mouse ( 1 button ) ?
distro: Ubuntu 5.10

would appreciate any help

---

### Post by linear on 2006-01-03
If I remember rightly, it's F12 (don't click the mouse button, just place the cursor where you want it and press F12).

---

### Post by diggs on 2006-01-04
buy a real mouse maybe?

---

### Post by CountChocula on 2006-01-04
f11 and f12 for sure

---

### Post by gdgardnerw on 2006-01-05
[QUOTE=linear]If I remember rightly, it's F12 (don't click the mouse button, just place the cursor where you want it and press F12).[/QUOTE]
This is correct. I used my one button mouse for about a week and then went and bought a $9.00 optical three-button mouse, which is much easier to use. You also have the advantage of the scroll wheel in the middle, which I find VERY useful. Well worth the $9.00!

---

### Post by dombleu on 2006-01-05
on:

[http://ardoino.altervista.org/blog/index.php?id=27](http://ardoino.altervista.org/blog/index.php?id=27)

i found:

[I]Trackpad configuration

To get it working use this driver by Stelian Pop Appletouch driver and take a look to my xorg.conf configuration file.

Now you could add to keys as left and right mouse buttons, so add these lines to /etc/sysctl.conf:
dev/mac_hid/mouse_button_emulation = 1
dev/mac_hid/mouse_button2_keycode = 97
dev/mac_hid/mouse_button3_keycode = 100
Now FN+CRTL and FN+ALT are the two mouse buttons.[/I]

a full reboot is needed ( or some service restart maybe... )

FN-ALT is not the best in the west, but it is better that F12! And It works pretty well indeed...

I use actually more my usb mouse than the touchpad anyway, but at least I can right-click easily when I'm left with the laptop alone.

Let me know if you find a more macOS style way.... It would sure be nice to just hold the click to get a contextual menu....

dom

---

### Post by nkbj on 2006-01-11
[QUOTE=dombleu]on:

Let me know if you find a more macOS style way.... It would sure be nice to just hold the click to get a contextual menu....

dom[/QUOTE]

I use the 'mouseemu' package from the 'Universe' repository with this setup (/etc/default/mouseemu):

MID_CLICK="-middle 125 272"         # Command key + mouse click
RIGHT_CLICK="-right 29 272"        # Control key + mouse click
SCROLL="-scroll 56"              # Alt key + mouse movement
TYPING_BLOCK="-typing-block 300" # block mouse for 300ms after a keypress

Regards,
Niels Kristian

---

### Post by frafu on 2007-07-16
Hello, 

An utility to open the contextual menu with a left click&hold is under development. It also has other features and is called mousetweaks and the contextual menu function can be activated under the 'delay click' tab. 

You can find the current version in [this thread]("http://ubuntuforums.org/showthread.php?t=494037"). But you have to compile it yourself; I am not able to build a debian package for this architecture, as I don't have a Mac with Ubuntu running on it. 

Any feedback will be appreciated. 

Francesco

---

