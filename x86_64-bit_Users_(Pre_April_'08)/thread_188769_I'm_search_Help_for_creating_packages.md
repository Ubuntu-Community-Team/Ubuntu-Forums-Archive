---
title: "I'm search Help for creating packages"
date: 2006-06-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Tarhan on 2006-06-04
Where i can found information about creating 64-bit packages for legacy 32-bit application? 
I'm beginner in creating packages. I failed in search information about creating packages in "Debian (Ubuntu) way" for 64-bit systems. If any one could help with links for such information i'll be glad. However, now i'm looking for subset of this information: how to install (and create packages) 32-bit applications (especially prorietary ones, which it's provided in binary form) in "Debian way" on  64-bit systems.

P.S.: Please, sorry for my poor English.

---

### Post by JoWilly on 2006-06-04
The docs for packaging are here: [https://wiki.ubuntu.com/DeveloperResources]("https://wiki.ubuntu.com/DeveloperResources")

Also check "checkinstall", which makes a deb package when you run "make install"

And "alien" which converts packages.

---

