---
title: "update broke my system (yet again)"
date: 2009-08-09
forum: x86 64-bit Users
---

### Post by LoneWolfJack on 2009-08-09
ok, since the latest update (it was wine and something else) I'm having major display issues. basically, this is a much more detailed version of another post in the general forum, hopefully, this doesn't qualify as cross-posting.

so: when I boot up, the monitor will temporarily shut off between the display of grub and the ubuntu loader progress bar and between that and the login screen.

I tried two variants:

normal boot:
-> GRUB
-> monitor goes temporarily off
-> ubuntu loader
-> monitor goes temporarily off
-> login screen
-> monitor goes black (but not power off) after logging in, but the desktop appears to be there because I hear the ubuntu theme and the mouse clicks

boot rescue system and pick "normal boot"
-> GRUB
-> monitor goes temporarily off
-> ubuntu loader
-> monitor goes temporarily off
-> monitor goes black (but not power off) and I blindly type username/pass
-> gnome comes up normal
-> any application that I try to launch through wine will cause the monitor to go black (but not power off)

my guess is that there's something fubared with the frequency setting ubuntu sends to the monitor because it does the typical "adjust frequency" quick on-off-thingy.

I tried disabling the restricted drivers and removing wine, both didn't help.

system:
ibex64, ATI 1800XT, compiz off

*help*

---

