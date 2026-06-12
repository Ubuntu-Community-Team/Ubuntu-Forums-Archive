---
title: "Gutsy Gettys CTRL+ALT+F1 through CTRL+ALT+F6 Not Workin"
date: 2007-10-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by Didjit on 2007-10-20
When I press CTRL+ALT+F1 through CTRL+ALT+F6, I do not get a login, but a blank screen with a blinking cursor. I can CTRL+ALT+F7 and get back to X fine.

Using Nvidia drivers. I think it may be a Nvidia driver related issue. Another issue, I do get a boot splash, however, after GDM logs in, I do not see a GNOME Splash (the little guy that pops up when the music starts), just a blank X screen, then the desktop loads.

Anyone else having these types of issues and has any tips to fix?

Thanks

Didjit

---

### Post by afeasfaerw23231233 on 2008-01-05
BUMMP! i 've got exactly the same problem! why no one answer this post for such a long time? buMMMMMMP!

---

### Post by devzero on 2008-01-05
I got F1 - F6 to work if I switched the splash screen off in the menu.lst

---

### Post by grozni on 2008-02-18
> **devzero said:**
> I got F1 - F6 to work if I switched the splash screen off in the menu.lst


Can you please post exactly what do did? Thanks

---

### Post by Tom'caT on 2008-02-18
Open terminal in Gnome (Accessories-Terminal). Enter sudo gedit /boot/grub/menu.lst. Enter your user password. Scroll down to the entry of your active kernel. You'll recognize that by the name you press every time you want to enter into Ubuntu. In the append section add "nosplash" or "splash=no" at the end of line, and if there delete the "splash=silent" or whatever it is there. Save the file and exit. Reboot.

---

### Post by afeasfaerw23231233 on 2008-03-21
i've just tried it and doesn't work

---

