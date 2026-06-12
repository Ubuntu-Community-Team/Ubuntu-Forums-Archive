---
title: "alien"
date: 2004-10-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by snowx1000 on 2004-10-22
Is there a way to alien 32bit rpms into compatible ubuntu amd64 packages?  Thanks.

---

### Post by jdong on 2004-10-30
no. Alien can't perform 32-bit to 64-bit conversions.

If you can find the source rpm, rebuild it to a 64bit RPM, then you can alien it into a 64-bit .deb

---

