---
title: "gutsy on full raid 1"
date: 2008-03-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by ruiruas on 2008-03-22
Hi,
I'm running gutsy 64 on a full raid 1 setup with two sata disks.
I've been getting aa occasional error during boot wich ends up in "initramfs". After rebooting, everything is normal again.
During startup, I can't reproduce the text, but it seems the system can't find the raid arrays or believes to find an invalid raid superblock. The truth is that after reboot everything works fine and that sometimes the startup goes without any error.

After checking the raid arays with the system running, everything is fine (using mdadm all arrays are synchronized)

This only happens in a system startup, never on reboots. When it happens again, I'll copy the error messages to this thread, until then, does anyone have a clue?

I once read something about the SATA disks needing more time on boot... what should I do?

Thanks.

---

### Post by dcstar on 2008-03-23
> **ruiruas said:**
> Hi,
I'm running gutsy 64 on a full raid 1 setup with two sata disks.
I've been getting aa occasional error during boot wich ends up in "initramfs". After rebooting, everything is normal again.
During startup, I can't reproduce the text, but it seems the system can't find the raid arrays or believes to find an invalid raid superblock. The truth is that after reboot everything works fine and that sometimes the startup goes without any error.

After checking the raid arays with the system running, everything is fine (using mdadm all arrays are synchronized)

This only happens in a system startup, never on reboots. When it happens again, I'll copy the error messages to this thread, until then, does anyone have a clue?

I once read something about the SATA disks needing more time on boot... what should I do?

Thanks.

Your /boot/grub/menu.lst file has a default timeout value, you might try increasing that to allow you hardware more time to settle down.

---

