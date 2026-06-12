---
title: "Intrepid poor disk preformance on encrypted root."
date: 2008-11-01
forum: x86 64-bit Users
---

### Post by Jwav3 on 2008-11-01
I run a encrypted root volume over a raid. Upon upgrading to Intrepid I'm seeing VERY VERY slow disk performance. Applications take an extreme time to launch, even the awesome bar in Firefox could take 60 seconds to appear.

System is also showing high load average, around 5+ 

Top shows kcryptd and kcryptd_io are eating up most of my 4 core processor. (however that is not abnormal.)

What changed and how do I fix it?

---

### Post by Jwav3 on 2008-11-01
Figured it out, AVG Antivirus.

sudo update-rc.d -f avgd remove

---

