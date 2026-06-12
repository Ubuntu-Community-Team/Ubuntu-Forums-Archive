---
title: "Boots to brown blank screen with responsive mouse?"
date: 2006-01-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by enzedchris on 2006-01-14
[QUOTE=OldMac]SORRY!  Abort abort abort! =)

Further sifting through older threads alerted me to the "date bug". I've altered the system date and the GUI startsup just fine now.[/QUOTE]


How do I change system date?

---

### Post by h3xx3r on 2006-01-14
[QUOTE=enzedchris]How do I change system date?[/QUOTE]
System...Administration.....Time & Date.

---

### Post by shawn12345 on 2006-01-15
You need to do a ctrl-alt-f1 (or 2,3,4,etc) use date -s to set date (man date for format), then ctrl-alt-f7 to return to X and it will start (or kill -9 xsession-manager and the gdm will restart)

---

### Post by ssam on 2006-01-15
good instructions [https://wiki.ubuntu.com/UbuntuDateBug](https://wiki.ubuntu.com/UbuntuDateBug)

---

