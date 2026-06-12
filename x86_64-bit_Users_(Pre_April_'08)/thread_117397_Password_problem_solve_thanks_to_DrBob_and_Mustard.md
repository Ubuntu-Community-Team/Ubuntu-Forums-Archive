---
title: "Password problem solve thanks to DrBob and Mustard"
date: 2006-01-14
forum: x86 64-bit Users (Pre April '08)
---

### Post by jeantasse on 2006-01-14
I found a solution to my "Password Problem".  I tried the "sudo" to do simple things like Update manager and it still did not work.  But as i keep on searching i found answers thanks to DrBob and Mustard.  Logins as root by opening a terminal: application/accessories/termial and after type in "su" and the root password to be able to do the "visudo" command and then you can had your username there and all the rights:

root	ALL=(ALL) ALL
jeantasse	ALL=(ALL) ALL

Save your work and all the: system/administration will be open for you.

To be safe you could create a new user with no rights to do your everyday work.  So thanks to you guys!!

---

