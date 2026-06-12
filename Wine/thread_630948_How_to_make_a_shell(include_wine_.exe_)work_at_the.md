---
title: "How to make a shell(include wine *.exe )work at the startup"
date: 2007-12-03
forum: Wine
---

### Post by BenBush on 2007-12-03
How to make a shell(include wine *.exe )work at the startup

---

### Post by sandman85 on 2007-12-03
I'm sorry, but your post was a bit unclear. Do you mean to ask how to automatically launch a Windows command terminal when you log in?

---

### Post by BenBush on 2007-12-04
> **sandman85 said:**
> I'm sorry, but your post was a bit unclear. Do you mean to ask how to automatically launch a Windows command terminal when you log in?

Yeah, you just said it, please tell me how to do it.

PS: Both my English and my native language are sometimes unclear, but it does not matter here, as the laptop language is always universal, so you can try to guess my meaning correctly.:lolflag:

---

### Post by Ferrat on 2007-12-04
Should be fairly simple just like a normal launch just do a normal script and add the wine command then the path to what you want to launch since the wine command is (if installed right) a systemwide command that can be launched from anywhere?

or do a launch script and add that to be launched at start up?

or am I wrong?

---

### Post by BenBush on 2007-12-04
I just have a change in mind, now I want my script to be started before logining in;

In other words, how to make my script be started when the  the GDM appears. (GDM is the GNOME Display Manager, a graphical login program. ):-({|=

---

### Post by cogadh on 2007-12-04
That shouldn't be done. That would require you to run Wine with root permissions which is a really bad thing to do. At best, all you should do is have something run at login with the current user's permissions.

---

