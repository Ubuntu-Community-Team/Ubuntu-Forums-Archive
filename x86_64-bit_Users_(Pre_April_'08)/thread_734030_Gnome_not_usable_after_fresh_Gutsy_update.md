---
title: "Gnome not usable after fresh Gutsy update"
date: 2008-03-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by saftaplan on 2008-03-24
[COLOR="#2e8b57"]The situation:[/COLOR]
Ubuntu 7.10 Desktop _AMD64_ on _Dell XPS M1530_, fresh and working install with _nVidia proprietary drivers_ (using nosplash option because of problems with framebuffer). I customized my Gnome-panel and some other Gnome-settings. Upgrade with update-manager right after install.

[COLOR="#2e8b57"]The problem:[/COLOR]
After rebooting when the system asks to, Ubuntu locks up after logging in. The desktop is still responsive but a bit slower (desktop right-click still works). 
Compiz still works. I can still launch applications (but ALT-F2 doesn't work). But the panel is empty most of the time. Some applets like user switcher, action bar and nm-applet still show sometimes and are responsive. Gnome-panel sometimes takes 100% CPU and when this happens, gnome-panel is still active when I log out. 
The theme of the few icons that sometimes show up is not Human but the gnome default theme. 
When the system starts I can see a flash of the normal gnome-panel contents, but then everything dissapears (I think this is because of compiz activating) and when the panel reappears, the contents are not redrawn.

[COLOR="#2e8b57"]What I tried:[/COLOR]
[LIST]
[*]I reinstalled, waited a week (because I thought it would be a temporary broken package), didn't customize settings and the problem was exactly the same. If I don't update the problem doesn't exist.
[*]Logged out, did rm -R ~/.* in console (deleted all my settings). Only after rebooting the panel looked like a non-customized one, but still wasn't responsive.
[*]I killed gnome-panel and it immediately restarts. This stops the 100% CPU problem (I don't have to kill -9 even if it takes 100% CPU so the process isn't totally locked up) but gnome-panel still isn't usable, most of the time two empty bars show up.
[*]I killed some other Gnome processes, with no success.
[/LIST]

This looks like a bug in Gnome because I did nothing special besides the nosplash option, just install and upgrade. I also enabled vesafb so that I did have a bootscreen, but I doubt that's got anything to do with it. Maybe I should try Hardy beta.

Can anybody help? Thank you.

[edit]Maybe it's unrelated but the system also hangs at "Shutting down ALSA" when shutting down. This is not the case if I don't update Gutsy[/edit]

---

### Post by dcstar on 2008-03-25
> **saftaplan said:**
> [COLOR="#2e8b57"]The situation:[/COLOR]
Ubuntu 7.10 Desktop _AMD64_ on _Dell XPS M1530_, fresh and working install with _nVidia proprietary drivers_ (using nosplash option because of problems with framebuffer). I customized my Gnome-panel and some other Gnome-settings. Upgrade with update-manager right after install.
.........

Simple test, edit /etc/X11/xorg.conf to use the inbuilt** nv** driver, if things then work the problem is with the "nVidia proprietary drivers".

---

### Post by saftaplan on 2008-03-27
Never mind - I really needed my computer so I installed Hardy beta and it works great (except for some stand-by issues). But thanks anyway.

---

### Post by Yellow Pasque on 2008-03-27
> **saftaplan said:**
> Never mind - I really needed my computer so I installed Hardy beta and it works great (except for some stand-by issues). But thanks anyway.
Awesome. I was going to recommend the Hardy beta as soon as I read the situation. :P
At this point, the Hardy beta is looking like a much better option for a lot of people with modern hardware.

---

