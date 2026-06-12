---
title: "Root password keeps resetting"
date: 2006-10-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by russianpirate on 2006-10-10
For some reason, from time to time when I start my computer up, the root password doesn't work, so I just reset it using sudo.

Why could this be happening?

PS: Also whenever the kernel updates, the computer cannot boot up because for some reason the splash doesnt work (i get error messages like ILLEGAL X86 OPCODE and it takes forever to start) and after I remove "slash quiet" from it, it starts up normally. Is there a splash package I need to install besides the kernel?

---

### Post by Kilz on 2006-10-10
> **russianpirate said:**
> For some reason, from time to time when I start my computer up, the root password doesn't work, so I just reset it using sudo.

Why could this be happening?

PS: Also whenever the kernel updates, the computer cannot boot up because for some reason the splash doesnt work (i get error messages like ILLEGAL X86 OPCODE and it takes forever to start) and after I remove "slash quiet" from it, it starts up normally. Is there a splash package I need to install besides the kernel?

I dont recommend setting up the root login and loging in as root. Because you open yourself to a whole lot of security problems. Why in this world are you booting to root so often? I hope your system is not comprimised.

---

### Post by russianpirate on 2006-10-10
i just installed ubuntu this weekend and i dont think its compromised.. im logging into root cause the kernel was just updated for some reason and i need to reinstall nvidia drivers

---

### Post by John.Michael.Kane on 2006-10-10
sudo dpkg -i (package name).deb
Or
Open synaptic enter you pass find said driver select it,and click apply.


Note: There should never be a need to run full blown root just to install a driver.

---

### Post by russianpirate on 2006-10-10
i understand but still why would my root password change randomly ?

---

