---
title: "Firefox leaves residues of Flash applets when force-quit"
date: 2008-01-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by Amurko on 2008-01-22
Many people seem to be having problems with Flash frequently crashing Firefox..  My problem,** in addition to that**, is that if Firefox crashes or has to be forced to quit while Flash is running causes the flash applets to remain stuck on my desktop.  They obstruct the view of icons and any new windows I open, and don't seem to go away unless I forcibly log out and log back in again, which is the most annoying part.

Note that I do not have this problem on my 32-bit machine running 32-bit Ubuntu.

I installed Flash on my 64-bit system using Automatix.

If you're still not sure what I'm talking about, try running "killall firefox-bin" while viewing a Youtube video in Firefox, preferably on Ubuntu 64-bit.

---

### Post by whoop on 2008-01-22
I have had that a couple of times. I use ps -A to retrieve the process id of npviewer.bin. Then I kill the process with kill <process id>

---

### Post by XplOzIOn on 2008-01-23
Hi there,

This also happens to me. While Watching FLASH "whatever" Firefox starts to hold while switching TABS or if you close it, it takes almost 2 minutes to close because theres some flash active.

Tried to reproduce this on 32Bit, but only happens in x64.

Cheers.

---

