---
title: "Getting 80x25 console on an iMac"
date: 2006-02-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by bmckee on 2006-02-23
New Ubuntu user here - but some previous linux experience.

I'm trying to use an old (233) iMac as a terminal replacement.
X isn't very useable with the ram available, but that's ok.

I need an 80x25 console rather than the framebuffer one that comes up as default.   Passing 'text' or 'vga16' to the kernel at boot seems to work for about a screenful of info on boot up, then it goes right back into framebuffer.

What do I need to do?

---

### Post by Ptero-4 on 2006-02-23
Putting it into the /etc/yaboot.conf should do it. Also disable usplash, it may be pushing the console back into fb mode.

---

### Post by bmckee on 2006-02-24
Hmm - still no go

I did try embedding text or vga16 and splash=no or no mention of splash at all in yaboot.conf,  and I did remove the usplash link in rc.2
Wait a minute - should I have removed it in rc.S too?

Watching the startup sequence - it flips to framebuffer long before it even mounts /

I think that means it's got to be a kernel thing doesn't it?

---

