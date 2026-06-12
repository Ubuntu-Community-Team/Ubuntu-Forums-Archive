---
title: "Running Wine Game with xinit problem"
date: 2014-03-23
forum: Wine
---

### Post by adec2 on 2014-03-23
Hi,

I am running an old game using playonlinux through xinit to provide a 16 bit display (which the game needs to run)
I use this command:

xinit /usr/share/playonlinux/playonlinux --run "Moto Racer" %F -- :1 -ac -depth 16

The game works fine doing this BUT the display of the game only takes up the top left quarter of the screen and the rest is black.
What's odd is i am using Kubuntu and have this problem but in a previous installation on Ubuntu it runs filling the full screen using exactly the same command.
Is there some little option I am missing here?

Thanks for any help

---

### Post by adec2 on 2014-04-20
Bump! Nobody?

---

### Post by bapoumba on 2014-04-20
.o/
Moved to Wine, where you may get more attention.

---

### Post by adec2 on 2014-04-20
I'll mark this as solved. I have found that there is a command line option to moto.exe -fullscreen. Doh!

---

### Post by bapoumba on 2014-04-20
> **adec2 said:**
> I'll mark this as solved. I have fund that there is a command line option to moto.exe -fullscreen. Doh!

lol, thanks. Sometimes, asking a question is enough to find a solution ;)

---

### Post by adec2 on 2014-04-20
Yeah i didnt think that running in a window was the problem i always presumed windows games from that era defaulted to full screen. Oh Well we live and learn!

---

