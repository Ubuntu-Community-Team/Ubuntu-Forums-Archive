---
title: "Ubuntu is crashing once in a while"
date: 2009-01-31
forum: x86 64-bit Users
---

### Post by xspace on 2009-01-31
I have a relatively fresh copy of intrepid 64, but once in a while out of the blue CPU usage goes to max and stays that way, and the mouse pointer barely moves, then I have to reboot.

Is there any way to look into this?

---

### Post by sanderj on 2009-02-01
I would not call this a crash, but a (almost) freeze.

Anyway: I would check which process is eating the CPU power: System -> System Monitor, and sort on CPU Time.
(or just 'top' on the command line).

Tip: start this command / tool right after logging on so that's it running as soon as the slow-down / freeze occurs.

---

