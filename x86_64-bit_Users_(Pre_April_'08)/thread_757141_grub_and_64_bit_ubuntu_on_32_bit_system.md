---
title: "grub and 64 bit ubuntu on 32 bit system?"
date: 2008-04-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by lackofcreativity on 2008-04-16
I plan to use an external hard drive and install DSL and 64 bit Ubuntu. Since DSL is 32 bit, I wanted it to use its GRUB for the bootloader, but it doesn't recognize Ubuntu if I install Ubuntu first. I have successfully dual-booted DSL and 32 bit Ubuntu on the same disk, using Ubuntu's GRUB. My question is: If I do it this way, will I be able to use the GRUB from the 64 bit Ubuntu to boot to DSL on a 32 bit system, or do I have to use some other bootloader that 32 bit systems can run? Aren't all versions of GRUB the same?

---

### Post by mick8985 on 2008-04-17
It doesn't make a difference, grub loads off its own microkernel, not your kernel so yes all grubs are the same. The only thing that changes are the grub commands which you run from your environment. Which aren't in /boot but in /bin or /usr/bin

---

### Post by lackofcreativity on 2008-04-17
Thanks!

---

