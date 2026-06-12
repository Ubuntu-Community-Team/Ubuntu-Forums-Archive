---
title: "Random console blanking"
date: 2009-11-13
forum: x86 64-bit Users
---

### Post by ErikAH on 2009-11-13
Hello, all.

I'm currently building a home server. I'm trying to use 64 bit Ubuntu Desktop 9.10 (fresh install) as the operating system, and I've run into a problem. At seemingly random intervals (fractions of a second to minutes) and for seemingly random periods (fractions of a second to perhaps a minute), the console goes blank / black. The longer the system runs, the more often and longer the blanking periods.

Superficially, this seemed like a thermal problem (it's brand new hardware), but I doubt it now for two reasons:

[LIST=1]
[*]The same problem occurs for either the on-motherboard video, or a VisionTek PCI express HD 4350 card.
[*]When the screen saver kicks in, the console unblanks if it's blanked, and doesn't blank again while the screen saver is active.
[/LIST]
I'm not having much luck finding similar issues and resolutions on the web or the forums. A couple days ago I found an article in which the author said a similar problem he had was solved by changing the compiz command line options, but I've lost track of the page and I don't recall the options he recommended.

Does this ring any bells for anyone? Anyone have a recommended debugging approach for the problem?

System basics: ASU P5QL-VM DO motherboard (Intel B43/ICH10D chipset), Intel Core 2 DUO E7500 CPU, 2 x 2GB RAM.

---

### Post by lemming465 on 2009-11-15
If you want to see if turning off the compiz stuff improves things, you can do that from System -> Preferences -> Appearance.  On the "visual effects" tab pick radio button "none".

---

### Post by ErikAH on 2009-11-17
Sadly, it doesn't affect the problem at all. Also, my statement that having the screen saver kick in would always unblank the console is incorrect. It's true most of the time, but not always.

---

### Post by robla on 2009-11-18
I'm seeing the same problem.  See:
[https://bugs.launchpad.net/bugs/397839]("https://bugs.launchpad.net/bugs/397839")

---

