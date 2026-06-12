---
title: "how to remove automatix for 7.04"
date: 2008-06-19
forum: x86 64-bit Users
---

### Post by j0eb0b on 2008-06-19
Even thought I have been at this long enough to graduate from newbie status, i have continued to use Automatix under 7.04 to help me get multi-media working.  In spite of the negative opinions of this package, it always helped me.  Well time and tide wait for not man.  I have upgraded to 8.04 and Automatix has folded the tent.  I want to properly uninstall Automatix from my machine.  No uninstall routine is included with the package.  What is the correct procedure to remove the old 7.04 compliant package from my new 8.04 system?

Thanks,
joe

---

### Post by nikgare on 2008-06-20
You could try:

dpkg -r automatix2

---

### Post by cariboo on 2008-06-20
You may have to manually edit your sources.list to get rid of all automatix changes.

Jim

---

