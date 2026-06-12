---
title: "End Session dialog, borked"
date: 2007-07-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by Onimae on 2007-07-29
So, basically, the End Session dialog doesn't display the options for Shutdown and Restart. Here is what I've done in the past few days:

I installed Compiz Fusion, using the fglrx drivers. Because of this I had to use xserver-xgl, and create an XGL session. Here is the script for that session (note that this should have put  a restart and shutdown button in the End Session menu):

```

#!/bin/sh
Xgl :1 -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session

```

For a while there, I did have the Shutdown and Restart button. Then I decided I would get Flash, but having a 64 bit architecture, needed to get FF32 (which later, I figured out wasn't true, but I digress). So I did that, and it would seem that after installing the 32 bit things and such the buttons disappeared.

Has anyone else had this  problem, or can anyone at least offer a helping hand? It's kind of annoying having to manually type in the shutdown command when I should be able to do it there...

**Peter**

---

### Post by Onimae on 2007-07-30
Anybody?

---

