---
title: "Ubuntu 9.10 Grub Error"
date: 2009-10-30
forum: x86 64-bit Users
---

### Post by yogiman.uk on 2009-10-30
Hi

Just installed 9.10 Karmic Koala, after install (went fine) the computer rebooted and GRUB started, then...

GRUB Load Stage 1.5
Grub loading please wait...
Error 15

Can anyone help me with this one please?

I have not got a clue, searched the forums for Grub error 15 and got no results.

Thanks for any help in advance.

Yogiman!

---

### Post by Dimarchi on 2009-10-30
You have more than one hard drive? In that case check whether you can switch boot priority in BIOS to some other hard drive than what it is now. I encountered the same problem after clean install reboot and solved it in the manner I described here.

---

### Post by clith on 2009-10-30
I'm having the "GRUB"-and-halt problem typical with multiple drives.

I managed to get my Ubuntu to boot by using a System Rescue CD, but when I try to tell Grub to use the right partition with:

```
grub-setup /dev/sdb4
```

I get an error about "core.img" missing from /boot/grub. Indeed, it isn't there. But it wasn't there before, either. What is it and where do I get one? :-)

Reid

---

