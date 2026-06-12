---
title: "E: system-tools-backends: (error)"
date: 2009-01-29
forum: x86 64-bit Users
---

### Post by lukaszr on 2009-01-29
Here's the error message i receive when installing programs via Add/Remove application. 
How do I fix this?

> E:system-tools-backends: subprocess post-installation script returned error exit status 1 

---

### Post by lukaszr on 2009-01-30
Bump!

---

### Post by Ayuthia on 2009-01-30
You might try:
```
sudo /etc/init.d/system-tools-backends stop
```
and try to update again.

---

### Post by lukaszr on 2009-01-30
> **Ayuthia said:**
> You might try:
```
sudo /etc/init.d/system-tools-backends stop
```
and try to update again.

i will try that. thanks!

---

