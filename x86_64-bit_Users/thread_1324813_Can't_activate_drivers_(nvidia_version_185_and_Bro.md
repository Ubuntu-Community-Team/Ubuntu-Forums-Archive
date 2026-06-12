---
title: "Can't activate drivers (nvidia version 185 and Broadcom STA)"
date: 2009-11-12
forum: x86 64-bit Users
---

### Post by Dread41 on 2009-11-12
When I try Broadcom, I don't get an error, but when I try to activate nvidia, I get the message, "SystemError: E:Unable to correct problems, you have held broken packages."
I am using an hp Pavillion dv9000 with a Broadcom BCM4328 and an integrated GeForce 7150m. I am running 64 bit Ubuntu 9.10.

---

### Post by Kilz on 2009-11-12
> **Dread41 said:**
> When I try Broadcom, I don't get an error, but when I try to activate nvidia, I get the message, "SystemError: E:Unable to correct problems, you have held broken packages."
I am using an hp Pavillion dv9000 with a Broadcom BCM4328 and an integrated GeForce 7150m. I am running 64 bit Ubuntu 9.10.

To fix the broken packages, open a terminal and type

```
sudo dpkg --configure -a
```

---

### Post by HappyFeet on 2009-11-12
You can also do:
```
sudo apt-get install -f
```

---

