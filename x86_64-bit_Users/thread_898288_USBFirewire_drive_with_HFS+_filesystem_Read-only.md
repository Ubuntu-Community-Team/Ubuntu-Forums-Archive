---
title: "USB/Firewire drive with HFS+ filesystem Read-only"
date: 2008-08-23
forum: x86 64-bit Users
---

### Post by Lars Noodén on 2008-08-23
I have a Verbatim Firewire/USB drive formatted as HFS+,
It's read-only despite being mounted read-write:
   /dev/sdb3 on /media/firewire type hfsplus (rw,nosuid,nodev,uhelper=hal)

So even mounted with the above settings, it's still only read-only:

 sudo touch /media/firewire/x
 touch: cannot touch `/media/firewire/x': Read-only file system

It's writeable from OS X...

---

### Post by LO Matt on 2008-08-23
Linux does not support write access to HFS+ if it's journaled.  I suspect that's your problem.  If you turn off journaling, you should be able to read write.

---

### Post by Sef on 2008-08-23
> Linux does not support write access to HFS+ if it's journaled. I suspect that's your problem. If you turn off journaling, you should be able to read write.

That is correct.  Read the [gentoo wiki]("http://gentoo-wiki.com/HOWTO_hfsplus") for more information.

---

