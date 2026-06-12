---
title: "problems installing involving IOAPIC ](*,)"
date: 2006-08-02
forum: x86 64-bit Users (Pre April '08)
---

### Post by anubis2814 on 2006-08-02
I don't know exactly what an IOAPIC is and what it does.  I have a Sempron 64 and the error I get when I try to install says, 
MP-BIOS bug: 8254 timer not connected to IOAPIC
any ideas?
](*,)

---

### Post by 3point2 on 2006-08-02
I've had the same problem with my AMD 3800+ . There's a fair number of other postings about it. Try adding 'noapic' to your kernel command line by editing /boot/grub/menu.lst .

---

