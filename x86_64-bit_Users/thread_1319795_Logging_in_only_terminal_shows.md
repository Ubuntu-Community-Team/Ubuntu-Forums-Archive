---
title: "Logging in only terminal shows"
date: 2009-11-08
forum: x86 64-bit Users
---

### Post by BigBig5 on 2009-11-08
When I log into Ubuntu only terminal shows at the top left corner. What do I do. I tried every thing I can think of. This never happen before. I get to many problems with 9.10.

---

### Post by bedtime_with_the_bear on 2009-11-08
> **BigBig5 said:**
> When I log into Ubuntu only terminal shows at the top left corner. What do I do. I tried every thing I can think of. This never happen before. I get to many problems with 9.10.

Sounds like you managed to enable failsafe login mode at some past point. I don't use Gnome so can't tell you exactly where to look, but when gdm starts, and before you attempt to log in, look for a button in kdm that lets you choose your session - you should probably have Default, Gnome, and FailSafe. Just select Gnome, enter your username and password and you should be back at your usual Gnome environment.

---

