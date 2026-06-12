---
title: "cpufreq - not working"
date: 2007-06-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by mpneerkaje on 2007-06-20
Hi All,

I'm running ubuntu 7.04 amd64 release on AMD Athlom X2 5000+. Using the Asus M2N-MX mobo.
Initially everything was working fine for few days until once i did some SW updates. Now while startup the ubuntu says 'cpufreq disabled as socket not supported'. If I try to run cpufreq-selector it says the same. 
because of this problem, my ubuntu always runs at full frequency.

The HW support is still there as frequency scaling is working in Windows XP.

Can anybody tell me how to make it working again?

Thanks in advance.

---

### Post by Kobalt on 2007-06-20
Hello,

Make sure you still have the *powernowd* package installed (and possibly reinstall it).

---

