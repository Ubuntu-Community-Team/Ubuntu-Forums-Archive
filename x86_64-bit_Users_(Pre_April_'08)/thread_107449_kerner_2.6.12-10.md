---
title: "kerner 2.6.12-10"
date: 2005-12-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by t_ras on 2005-12-23
just accepted auto-update to new kerner (2.6.12-10) and gnome session is not able to load anymore. It fails on ICE not finding TCP and authority file (or something like this).
I tryed exaping at reboot and choosing 2.6.12-9, but it didn't help.
Any Idea how to solve it (reinstalling ICE through apget?)? or how to return my old kernel properly?

Thanks

---

### Post by t_ras on 2005-12-23
I managed to solve it by changing permissions to ICEauthority file, but now it works only with 776 (formerly it seems to have been 600).

Any Ideas why it happened?

---

