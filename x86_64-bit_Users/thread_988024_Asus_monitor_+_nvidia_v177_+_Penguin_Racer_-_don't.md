---
title: "Asus monitor + nvidia v177 + Penguin Racer - don't work"
date: 2008-11-20
forum: x86 64-bit Users
---

### Post by merito on 2008-11-20
Hi

I've got Ubu 8.10 x64 on my desktop and I've got a problem. When I run Planet Penguin Racer I see small window with text: OUT OF RANGE. This message is not from Ubuntu, but from my Asus monitor. I don't know what's going on. When I use Ubuntu not in game all it's OK. I've got nvidia driver v177. Unfortunatly I don't have second monitor to check this problem.

Regards
merito

---

### Post by ARPanah on 2009-01-03
> **merito said:**
> Hi

I've got Ubu 8.10 x64 on my desktop and I've got a problem. When I run Planet Penguin Racer I see small window with text: OUT OF RANGE. This message is not from Ubuntu, but from my Asus monitor. I don't know what's going on. When I use Ubuntu not in game all it's OK. I've got nvidia driver v177. Unfortunatly I don't have second monitor to check this problem.

Regards
merito


You can change display settings manually.
Just open:

**~/.ppracer/options**

and edit the line where it says:

***set fullscreen true***

to:

***set fullscreen _false_***

Now run ppracer. You can now change settings on the screen.

---

