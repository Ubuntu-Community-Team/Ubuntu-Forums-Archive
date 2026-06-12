---
title: "WINE no longer using virtual desktop size"
date: 2013-07-05
forum: Wine
---

### Post by lordbah on 2013-07-05
I was using wine1.5-20 on Ubuntu 12.04 64bit, had it emulating a virtual desktop, size 1900x1050, in which I ran a game. It worked. Today I upgraded to Ubuntu 13.04. Now wine is ignoring the virtual desktop size. It still opens inside a window like it used to but the window is now much smaller - perhaps 1280x1024 - and unresizeable, as it was before. I uninstalled wine1.5 and installed 1.6-rc4. No difference. winecfg is happy to let me change the virtual desktop size but it never has any effect, either when running the game or just "wine notepad.exe". A search found one post which said to edit user.reg and under "X11 Driver" set "Desktop"="WxH", which I tried, but it also had no effect - and I see that winecfg is not writing the configured size to that file either. Any notion what's going on here?

---

### Post by lordbah on 2013-07-05
Okay, changes made in winecfg are in fact being written to user.reg - after a delay of several seconds. I don't understand why I can't observe this via strace winecfg or wineserver, or where the delay comes from, but the data does get there eventually. However, wine appears to be truncating any width greater than ~1200 and any height greater than ~1000. My display is 2048x1152, so naturally I want to use most of that width.

---

### Post by lordbah on 2013-07-05
I don't think this is wine's doing, I think it's something with X or compiz or unity. xeyes -geometry 1240x999 gives me a window about half the width of my screen and most of the height. xeyes -geometry 1640x999 gives me the exact same size window. xeyes -geometry 1240x1000 gives me a window which is maximized.

---

