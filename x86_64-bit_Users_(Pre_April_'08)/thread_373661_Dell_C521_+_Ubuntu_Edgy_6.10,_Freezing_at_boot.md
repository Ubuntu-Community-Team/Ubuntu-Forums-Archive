---
title: "Dell C521 + Ubuntu Edgy 6.10, Freezing at boot"
date: 2007-03-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by justinshattuck on 2007-03-01
I just unwrapped a Dell C521 workstation with an AMD64 processor.  I downloaded the Ubuntu-6.10-amd64 iso file from the alternate cd and attempted the installation.  However, upon the Ubuntu installaton screen appearing, autoselecting start installation -- it freezes on the black screen with the grayscale logo for Ubuntu.

It just sits, cdrom stops spinning, hard-disk stops spinning up etc.

Recommendations?

---

### Post by justinshattuck on 2007-03-01
I added `acpi=off`

---

### Post by justinshattuck on 2007-03-01
Okay, I got it installed, using live cd with boot string, acpi=off, however, now that its installed it won't boot properly, it hangs like before.

help!

---

### Post by SaddisticTwist on 2007-03-01
Boot using the LiveCD

In a terminal type;

[INDENT]sudo gedit /boot/grub/menu,lst[/INDENT]

Note: lst is a small letter L

Look for the line kernel, there should be a few and change the 1st one.

Example (Add the acpi=off) :
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda2 ro quiet acpi=off splash

Then save, and reboot normally.

---

