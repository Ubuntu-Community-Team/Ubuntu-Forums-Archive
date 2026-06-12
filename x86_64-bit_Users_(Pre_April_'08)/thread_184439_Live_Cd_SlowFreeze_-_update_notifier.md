---
title: "Live Cd Slow/Freeze - update notifier?"
date: 2006-05-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by helpdeskdan on 2006-05-29
The live CD is fine for a couple minutes after which it suddenly slows/freezes for several minutes.  Then, suddenly, the update notifier pops up with tons of updates and things seem better.  (Why is this even ENABLED on the live CD?!!)  I highly suspect this to be the cause of my grief.  Perhaps a carefully placed killall could sovle this?

Surely I am not the only person having this problem; I've googled it with no results.

---

### Post by ssam on 2006-05-30
it is possible to install updates and new software on the live cd. the filesystem is writable using some magic and you system ram. its more useful for testing software not installed on the cd than for updating it.

which live cd are you using? i though they had turned this off in dapper.

---

### Post by helpdeskdan on 2006-05-30
Dapper, eh?  Thanks for this advice; I'll give it a whirl. :) 

Enabling update notifier was not wise on a live cd.  Even if I wanted to update, I could just do a apt-get update!  The file system is writable, but it's RAM!  The more you write, the more your RAM fills up!  Those updates take quite a bit of memory!

---

