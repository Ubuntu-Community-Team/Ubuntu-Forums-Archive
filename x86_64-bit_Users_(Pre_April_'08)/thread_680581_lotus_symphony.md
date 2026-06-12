---
title: "lotus symphony"
date: 2008-01-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by prince_niceguy on 2008-01-28
is any one able to install lotus symphony on 64bit? I have tried doing it but it gives me error and creates some files on my system. But there is no executables which i use to launch this.

I am attaching the error logs during the install.

---

### Post by crjackson on 2008-01-28
BUMB because I'd like to know too...

---

### Post by old_salt on 2008-02-14
Same here. I'm unable to install period and I do have Java installed. Just wished Java would go away. What a lousy language.

---

### Post by pecanov on 2008-02-18
Throwing java away would mean throwing 50% of quality applications that actually work on linux (openoffice, eclipse, azureus, limewire and hundreds more).

Installing java just simply doesn't solve the problem that you are installing a product bundled with it's own 32-bit distribution of Java on a 64-bit system. Try solving the problem there.

---

### Post by ycg on 2008-06-12
> **pecanov said:**
> Throwing java away would mean throwing 50% of quality applications that actually work on linux (openoffice, eclipse, azureus, limewire and hundreds more).

Installing java just simply doesn't solve the problem that you are installing a product bundled with it's own 32-bit distribution of Java on a 64-bit system. Try solving the problem there.

You made a good point but, I'm running Visualparadigm for UML from the 32 bit installer on my amd64 install, and it works just fine... why symphony are not? where should I look to fix this?  any idea??

---

### Post by munzli on 2008-06-17
hi

did you run the setup as root? 

you also need to install libstdc++5
```
sudo aptitude install libstdc++5
```

after running the setup i had to change the permission to the files (i.e. ~/.lotus)
```
sudo chown -R  youruser:youruser *
```

---

