---
title: "Busy Box?"
date: 2008-08-08
forum: x86 64-bit Users
---

### Post by Kaisen on 2008-08-08
So, I've been running Ubuntu for about 3 weeks now, I've had to reformat it about 4 times because of some boot problem. It's randomly deciding to dump me to a menu of sorts, with the words BusyBox. I'm not really sure what it is, but I'd like it fixxed...I don't want to reformat every time it happens. The weird thing is that I was doing nothing different at all, when I last turned it off. I just restarted and booted to windows, to update some stuff for a game I play. When I restarted windows and booted Ubuntu, it did it AGAIN. This is the fifth time it's happend. I'm not sure why it's doing this or if there's a way to fix it.


So if you've got any info you can toss my way, I'm definatley open to learning. Thanks.

---

### Post by flytripper on 2008-08-09
same here. i installed ubuntu by wubi. i installed nvidia drivers and awn. rebooted and pow!! sucker punch to the balls, it boots to busy box whatever the hell that is. no ubuntu to be found.. pleeeease help

---

### Post by underground on 2008-08-10
When in the menu highlight the start or install ubuntu option and press F6 for other options
add after -- the following
all_generic_ide floppy=off irqpoll pci=nomsi

Had the same problem as you and solved it doing the above..
hope i helped you.

---

### Post by jpkotta on 2008-08-11
Don't know how to fix your problem, but I can tell you what busybox is.  It's a single program that combines many different utilities that are usually separate programs.  It's much smaller and more limited than the programs it replaces.  It is used in embedded systems (like wireless routers, if they run Linux) and in this case, a minimal recovery system.  IIRC, busybox is in the initrd, which gets booted by grub and in turn boots the main OS; something in there is failing and it drops you to a busybox shell.  The point is, you (& forums) might be able to figure what's wrong from the boot messages or from the bb shell.  

In grub, try editing the kernel line.  Press "esc" to get the menu, press "e" to edit the entry, and press "e" again to edit the kernel line.  Delete the "quiet" option and boot with "b".  See if there are any serious looking errors.

---

