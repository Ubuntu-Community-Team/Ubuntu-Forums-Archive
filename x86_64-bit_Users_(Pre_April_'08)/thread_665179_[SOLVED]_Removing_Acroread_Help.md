---
title: "[SOLVED] Removing Acroread Help"
date: 2008-01-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by chrism66 on 2008-01-12
I made a mistake and installed the current version of Acroread. I would like to un-install it. It is not in the Synaptic, and when I run sudo apt-get remove acroread it says " Couldn't find package acroread" Ant way of getting it out of my box? Thanks!

Chris

---

### Post by Kilz on 2008-01-12
> **chrism66 said:**
> I made a mistake and installed the current version of Acroread. I would like to un-install it. It is not in the Synaptic, and when I run sudo apt-get remove acroread it says " Couldn't find package acroread" Ant way of getting it out of my box? Thanks!

Chris

Exactly how did you install it?

---

### Post by chrism66 on 2008-01-12
I followed the instructions on your web page to install it.

---

### Post by Kilz on 2008-01-12
This should do the trick

```
sudo rm -rfd /usr/local/Adobe
```

---

### Post by chrism66 on 2008-01-12
Thanks!  Kilz worked like a charm.

---

