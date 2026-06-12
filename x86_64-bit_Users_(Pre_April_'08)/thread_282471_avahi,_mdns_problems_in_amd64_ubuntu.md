---
title: "avahi, mdns problems in amd64 ubuntu"
date: 2006-10-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by lenst on 2006-10-22
I have problem getting avahi working in my ubuntu 6.06 amd64, it works well in my i386 installation. Also mdns-scan fails with an error in amd64.

I checked network trafic with ethereal, and restarting the avahi-demon produces no trafic in amd64 but a lot of mdns trafic in i386.

Any ideas? Could the ethernet interface some how not allow multicast in my amd64 installation?

---

### Post by lenst on 2006-10-31
Problem solved, it had nothing to do with amd64. I had forgot that you need to hack the firestarter config to get avahi to work (with firestarter).

---

### Post by factor on 2006-11-01
lenst: what have you changed exactly in firestarter config for avahi to work?

---

