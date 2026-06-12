---
title: "ACPI cannot load system description tables"
date: 2006-07-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by anubis2814 on 2006-07-25
I have never heared of a acpi before, I have a new sepron and can't install linux 32 or 64 on it need help

---

### Post by hizaguchi on 2006-07-26
Acpi is software power management.  Some computers don't work well with it and need to use apm (which lets the bios manage the power settings) instead.  You need to boot with acpi=off or noacpi or something like that.  Stick in the disk and hit (I think) F6 to see more boot options and pick the one that disables acpi.

Once the install is done, you may or may not be able to boot with acpi enabled.  If you end up with an unbootable system, you can disable acpi at the grub menu by selecting the kernel you would normally boot, hitting "e", moving down to the "kernel" line, "e" again, then adding "acpi=off" at the end, then hit enter and then "b" to boot.  You should be able to get into your desktop then, but that's only a temporary fix.  To keep from having to do that every time you reboot, you need to edit /boot/grub/menu.lst the same way.  There's also a grub update tool that is a little better for doing that part so you don't have to redo it for every kernel update.

---

### Post by simonrose on 2007-12-06
I'm having a similar problem. I am running latest version, 7.10. Everything has been running fine and then yesterday just after the grub loading screen it printed:
ACPI: Cannot load system description tables

It also posted some stuff about pnpbios being turned off, I went into my bios and turned it off and also used the command from the post above (acpi=off) now when it boots after that I get a screen that just says: Starting up ...
That is it. It doesn't go any further.

Anyone got any ideas?

Simon

---

