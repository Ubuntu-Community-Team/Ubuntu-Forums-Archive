---
title: "AMD64 Grub Install"
date: 2005-01-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by martyr on 2005-01-25
When installing grub from the AMD64 Warty CD, it does neither find any other operating systems installed on my machine nor does it ask where to install grub on. It simply writes it on the mbr without asking.

Maybe it'd be more convenient to let the user decide (just as for the i386 architecture).

---

### Post by valadil on 2005-01-25
That's odd.  It asks in hoary.

You can edit /boot/grub/menu.lst to give yourself access to other OSes.

just add the following lines:
title              Other OS (probably windows)
root              (hd0,0)
makeactive
chainloader    +1
boot

Note that the root line should point to a different partition on your system.  I keep windows (mainly for halflife 2 and adobe premeire) on the first partition on my first disk.

---

### Post by martyr on 2005-01-25
I thought that wouldn't work on NT-based Windows operating systems?
Say I have Windows XP (preinstalled) on my notebook and want to add ubuntu to another partition. If I install AMD64, it kills the mbr and thus the NT bootloader.

This is no real problem to me, as I will most probably be forced to use the i386 version because of wlan drivers being unavailable for amd64 anyway. I just thought that users would generally welcome control over where grub gets installed :)

---

