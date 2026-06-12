---
title: "Edgy upgrade lost 64bit"
date: 2006-11-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by rebird242 on 2006-11-23
So I recently upgraded to Edgy using the prescribed method...

"If the upgrade is performed on a system without update-manager (e.g. on a server). The upgrade must be done in two steps. The first run of apt-get dist-upgrade will upgrade everything except for upstart. After this a second apt-get dist-upgrade will finish the upgrade."

Everything is fine but kinda screwy. First off I noticed my Kernel is "linux-generic" and not linux amd64 like before when i click that kernel it says its obseleted by linux generic. I get the feeling thats wrong.

Do you guys know how to fix this?

---

### Post by keybuk on 2006-11-23
> **rebird242 said:**
> So I recently upgraded to Edgy using the prescribed method...

"If the upgrade is performed on a system without update-manager (e.g. on a server). The upgrade must be done in two steps. The first run of apt-get dist-upgrade will upgrade everything except for upstart. After this a second apt-get dist-upgrade will finish the upgrade."

Everything is fine but kinda screwy. First off I noticed my Kernel is "linux-generic" and not linux amd64 like before when i click that kernel it says its obseleted by linux generic. I get the feeling thats wrong.

Do you guys know how to fix this?

generic is the correct kernel.  This is the optimised kernel, which will perform best on your system.

The alternative kernels are for older processors only.

Yes, the name sucks

---

