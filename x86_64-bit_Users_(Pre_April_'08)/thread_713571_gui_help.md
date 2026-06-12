---
title: "gui help?"
date: 2008-03-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by the_clap on 2008-03-02
hey guys, noob here. 
i've got a problem at startup, i tried to fool my monitor into a higher resolution than it natively supports, but now i'm stuck in terminal mode. is there any way to fix this, and if so how?
remember, i'm a linu-noob so you may have to explain things to me carefully
Thanks!

---

### Post by kuja on 2008-03-03
For the time being you can reconfigure X with this command: "sudo dpkg-reconfigure xserver xorg"

If it's not accepting the higher resolution maybe it's a video driver issue? What card do you have and what driver are you having X use for it? (you can find about by running this command: "grep Driver /etc/X11/xorg.conf")

---

