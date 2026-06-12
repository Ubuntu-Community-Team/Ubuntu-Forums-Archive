---
title: "Source list not being read!"
date: 2009-06-13
forum: x86 64-bit Users
---

### Post by xtjacob on 2009-06-13
I have a Acer Aspire 4530 and it has Ubuntu 9.04 x86 64-bit on it. I turned it off and when i turned it back on it said that it couldn't read sources.list. I tried to open it by using
 ```
sudo gedit /etc/apt/sources.list
```
but when i tried to save it it said that the file didn't exist. Even when i add sources in the Software Sources section under system/administration it still doesn't show up! Please help!

---

### Post by oldos2er on 2009-06-14
Can you post the output of **ls /etc/apt/** ?

---

### Post by cariboo on 2009-06-14
You need to use gksu to open a graphical program. Press Alt-F2 and type:

```
gksu gedit /etc/apt/sources.list
```

---

