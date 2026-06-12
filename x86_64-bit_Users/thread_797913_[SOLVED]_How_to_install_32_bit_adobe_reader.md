---
title: "[SOLVED] How to install 32 bit adobe reader?"
date: 2008-05-17
forum: x86 64-bit Users
---

### Post by Vicfred on 2008-05-17
I downloaded the deb but I doesn't install is there a way to install it?

---

### Post by joshsmith on 2008-05-17
check out medibuntu :) it has the package

---

### Post by Vicfred on 2008-05-17
nvm I just found the solution I made this:

```
sudo dpkg -i --force-architecture AdobeReader_enu-8.1.2-1.i386.deb
```

(obiously on the folder that I downloaded the deb from Adobe site)

btw I don't any problem with the default pdf viewer or ePDFview but i love adobe reader design <3

---

### Post by joshsmith on 2008-05-17
to be honest you should probably unisntall that and try medibuntu
having a forced 32 bit package when it is not needed could cause you troubles later. medibuntu is a lot safer

---

### Post by Sef on 2008-05-17
> to be honest you should probably unisntall that and try medibuntu
having a forced 32 bit package when it is not needed could cause you troubles later. medibuntu is a lot safer

No, the op shouldn't.  If adobe has been installed and works, then best to leave things as they are.

---

### Post by Kilz on 2008-05-17
> **joshsmith said:**
> to be honest you should probably unisntall that and try medibuntu
**having a forced 32 bit package when it is not needed could cause you troubles later**. medibuntu is a lot safer

Nope, as long as its not a library. You should be able to remove it  easy enough.

---

### Post by jocko on 2008-05-18
> **joshsmith said:**
> to be honest you should probably unisntall that and try medibuntu
having a forced 32 bit package when it is not needed could cause you troubles later. medibuntu is a lot safer

> **Sef said:**
> No, the op shouldn't.  If adobe has been installed and works, then best to leave things as they are.

But will forcing install of a 32 bit package automatically bring the needed 32 bit libraries?
The "64 bit" acroread package in medibuntu really is 32 bit, but it's dependent on the ia32-libs.

---

