---
title: "[SOLVED] dpkg was interrupted, you must manually run 'dpkg"
date: 2008-09-12
forum: x86 64-bit Users
---

### Post by fminmexico on 2008-09-12
After installing Ubuntu 64 I had 101 updates to install,when I try to install them I get. (E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
What is this.
                fminmexico.

---

### Post by Joeb454 on 2008-09-12
Open a terminal and enter ```
sudo dpkg --configure -a
```

When asked for your password - enter it, though it won't show any characters being entered :)

---

### Post by fminmexico on 2008-09-12
> **Joeb454 said:**
> Open a terminal and enter ```
sudo dpkg --configure -a
```

When asked for your password - enter it, though it won't show any characters being entered :)

Thank you very much terminal is now installing.
                 fminmexico.

---

### Post by youjianrong on 2009-04-02
Thanx u very muuuch Joeb454):P

---

