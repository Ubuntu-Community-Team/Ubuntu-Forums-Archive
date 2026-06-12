---
title: "How to play DVDs in 64 bit Feisty?"
date: 2007-07-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by marco123 on 2007-07-08
Hi.  Please help!  

I've set up 64 bit Feisty, even got flash working on Firefox thanks to a wonderful script posted by some guru on these forums, but I'm stuck on DVD playback.

I've tried installing all the "libdvd" packages from Synaptic like in the 32 bit but it won't work.

Has anyone got DVD's working on 64 bit Feisty that can help me set it up?

Thanks, Marco.

---

### Post by marco123 on 2007-07-08
Update - I can play old DVD'd without menus now, but no new ones with menus.

---

### Post by marco123 on 2007-07-08
Resolved!

For anyone that is stuck, try installing the "libdvd" packages from Synaptic, and then run these 2 commands in the terminal -

sudo apt-get install debhelper build-essential fakeroot

then -

sudo usr/share/doc/libdvdread3/install-css.sh

---

