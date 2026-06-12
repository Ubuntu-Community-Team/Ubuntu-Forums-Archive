---
title: "Key Input Broke after Update"
date: 2008-01-26
forum: Wine
---

### Post by Statix0 on 2008-01-26
Today I updated to 9.54 with the update manager and my keyboard input in all my wine applications fails. No hotkeys work in games, and not even notepad outputs anything. Keys still work in Ubuntu obviously, and when I did a "search" in notepad it still worked if that means anything. I don't know really know what other details to give. There are no terminal errors.

---

### Post by Ferrat on 2008-01-27
sounds like some driver or similar is broken in your new installation of wine, try to reinstall it

---

### Post by Statix0 on 2008-01-27
I discovered the problem. When I typed with an application open it would go into the terminal, in other words it wasn't going to the right window. Turning "Allow window manager to control the windows" ON in winecfg (which is weird, because I heard it was better with it off) fixed the problem.

---

