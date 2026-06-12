---
title: "[SOLVED] Rare problems"
date: 2007-11-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by Luis Macias on 2007-11-21
Hi, my ubuntu worked fine but now when it starts a message appears telling an internal error occured ald Hal or something like that couldnt start, i dont have internet anymore, no battery display in tool bar, and many apps wont start, any idea of what could be causing these problems?

Thanks

---

### Post by Luis Macias on 2007-11-22
I checked the error says " An internal error occured, couldn´t start HAL!", please can anyone help me because gutsy freezes i cant do anything on it. Thanks

---

### Post by damvcoool on 2007-11-22
can you reinstall without wiping your Data?? do you have your home directory on a separate partition from root?

have you gonne into recovery mode and then typed reboot??

suggestion.

go into recovery mode, and after you have the promt type reboot, that will shutdown ubuntu properly and maybe you will have HAL running nice agian.

if that does not work, go into recovery mode, and type ```
apt-get reinstall hal dbus libhal1 udev
```

this will basically reinstall the Hardware Abstraction Layer

---

### Post by Luis Macias on 2007-11-22
I solve the problem, what happened is that i changed in 

sudo gedit /etc/init.d/rc

i changed CONCURRENCY=none for shell, because some page said this would accelerate boot, but instead caused this problem, so i just changed again for none.

Thanks for the help anyway

---

