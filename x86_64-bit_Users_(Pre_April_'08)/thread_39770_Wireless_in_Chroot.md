---
title: "Wireless in Chroot"
date: 2005-06-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by mthaddon on 2005-06-06
Can anyone help me out in getting wireless configured in my 32bit chroot? I have it installed and working fine in 64bit, but not yet in 32bit. At the moment I modprobe ndiswrapper manually in 64bit as I don't use wireless that much. Would it be easier if I just configure it to automatically load? Is it effectively using two wireless connections, or one?

Thanks, Tom

---

### Post by mthaddon on 2005-09-30
Turned out it was that the DNS wasn't being set correctly. Just had to edit /chroot/etc/resolv.conf and everything was okay.

---

