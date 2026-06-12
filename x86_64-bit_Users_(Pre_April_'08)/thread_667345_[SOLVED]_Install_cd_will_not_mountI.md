---
title: "[SOLVED] Install cd will not mount?I"
date: 2008-01-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by Wraith2058 on 2008-01-14
I am currently running Fedora 8 on my linux comp with the only problem is that it is Fedora and as such not a userfriendly i one would like.  My problem is that when i downloaded the install cd for Ubuntu it mounts then my screen goes into standby.  to fix this i downloaded the textbased installer and was able to install however postinstall same problem screen in standby.  The funny thing is that i can boot in recoverymode and start X as root.  any insite to the problem would be great.

My Hardware
Asus A8N-E nforce4 ultra chipset
Asus ATi x800xl PCI-E x16
AMD 64 x2 4800+

---

### Post by tgalati4 on 2008-01-15
Could be a splash screen problem.  When grub loads, hit "e" to edit the line and remove *quiet* and *splash*.  Pay attention to the bootup messages to see where it is hanging.

---

### Post by Wraith2058 on 2008-01-15
I dont belive that it is a grub problem i think it is a X problem i misttiled the thread so i am just going to creat a new one with a better heading.  and the reason i belive it is an x problem is becsuse the same thing happens when i try to boot a slaxware live cd the cd mounts and begins to boot and then nuthing.

---

### Post by 6568912 on 2008-01-15
try booting in safe mode? it helps in a lot of problems >_>

---

