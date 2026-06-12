---
title: "msttcore fonts trouble"
date: 2008-08-13
forum: x86 64-bit Users
---

### Post by ayushjsh on 2008-08-13
Im currently working on Ubuntu 8.04
i get this error every time i use any of the install managers....
E: msttcorefonts: subprocess post-installation script returned error exit status 1
this is the error i get whenever i try installing any of the packages.
i have a custom theme running from gnome.art.org
please help as this is causing a lot of my applications to behave irksome.
thanks

---

### Post by oldos2er on 2008-08-13
In a terminal, type "sudo aptitude install -f" followed by "sudo aptitude update".

 If that doesn't help, please post back.

---

### Post by ayushjsh on 2008-08-13
thank you very much for the solution...
well it helps me with one thing now , that the packages are installed correctly
even though the error msg till shows.
one more thing i would like to add is that i added the mac4lin application and its fonts too...could it be because of that....
the error still remains

---

### Post by oldos2er on 2008-08-14
I'm not sure why you're still getting the error. Can you go into Synaptic Package Manager and try reinstalling msttcorefonts?

---

