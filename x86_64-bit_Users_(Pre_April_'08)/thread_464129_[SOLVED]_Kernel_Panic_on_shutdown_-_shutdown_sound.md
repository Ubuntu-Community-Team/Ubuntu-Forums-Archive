---
title: "[SOLVED] Kernel Panic on shutdown - shutdown sound endless loop"
date: 2007-06-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by daimaru on 2007-06-04
this problem only exists for me when using the 64-bit version of ubuntu i386 does not have the problem.
so on 64-bit the problem started with kernel panic on boot right after grub menu. --> computer freezes capslock led starts blinking. totally unresponsive have to use reset to reboot.
in recovery mode computer starts normally, startx gets me to my graphical desktop. no problems. shutting down in recovery mode works too.

in normal mode after solving the start freeze bug (found the solution for the boot-freeze problem on [_[COLOR="Red"]launchpad[/COLOR]_]("https://bugs.launchpad.net/ubuntu/+bug/86666")) i now have the same problem when shutting down. --> computer freezes capslock starts blinking and the shutdown sound is stuck in a endless loop. 

i've read somewhere that this might be a problem with the xorg-fglrx drivers. I'm using the restricted drivers not the ati manually built ones. Before i start building the drivers manually i wanted to ask if anyone already found a solution to this problem? PLZ help because my 64-bit system is definatly running faster the the i386 (y i switched).

by the way for people with same problem: boot freeze solution:
add vga=792 to default and kernel options in /boot/grub/menu.lst
or turn off splash

---

### Post by daimaru on 2007-06-04
anyone got any ideas at all on this ?

---

### Post by daimaru on 2007-06-04
bump chakachaka bump ... come on no one as this problem?

---

### Post by Cappy on 2007-06-05
Go to your GRUB line and take out the "splash" line and ALSO the "VGA=" line you added. You must remove BOTH from the /boot/grub/menu.lst line or else it won't work.

---

### Post by daimaru on 2007-06-05
thx cappy that did the trick, can now shutdown without problems . thx again.

---

