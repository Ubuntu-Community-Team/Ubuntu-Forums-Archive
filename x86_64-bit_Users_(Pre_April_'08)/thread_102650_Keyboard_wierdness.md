---
title: "Keyboard wierdness"
date: 2005-12-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by pauljwells on 2005-12-12
I have Breezy on an AlPB 12". Most of the time, at bootup, the keyboard behaves 'properly', that is the shift and caps lock keys do what you'd expect. The " and @ are swapped compared to the keyboard markings, ie shift-' gives @ and shift-2 gives " just like on a 'normal' keyboard.

But then, something strange happens, and I haven't yet found out what triggers it... The shift key stops working. To get capitals I have to use Caps-lock. To get the symbols on the number keys (!"£$%....) I have to use caps-lock AND shift...

...but wierdest of all is that is when it is in this strange mode, the " and the @ swap back to where the mac keyboard says they are!

I've tried a few obvious things (change keyboard in 'preferences, that sort of thing) but the only way to restore the shift key is to reboot.

Anyone any idea why this happens?

---

### Post by autocrosser on 2005-12-12
Take a look at your /etc/X11/xorg.conf & see if the keyboard preference is "pc105" or "macintosh"---if it is the pc105, change it and restart your X server.  You might get a message that Gnome & X server settings are different--if so, tell it to use the X server & don't ask again----

---

### Post by wanderfowl on 2005-12-12
Are you using GDesklets?  It's managed to hijack the shift-key on me until I changed the float shortcut in preferences.

---

### Post by pauljwells on 2005-12-13
Thanks for the responses!
I'm pretty sure that my xorg.conf has macintosh already, but I'll check.
For sure, I did open GDesklets and I think all the other times it happened I had GDesklets going too. I'll take a look at the preferences.

Many thanks autocrosser and wanderfowl.

---

