---
title: "help me!!!"
date: 2007-09-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by hiruma on 2007-09-08
i've some problem here...when open my sypnatic package manage this thing appear

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

because my notebook battery was weak while i'm upgrading something.. 
what should i do...

---

### Post by PilotJLR on 2007-09-08
Do what it says to do... open a terminal and run
```

sudo dpkg --configure -a

```

---

### Post by luisromangz on 2007-09-08
You should do exactly what the error message tells you to do, which is to open a terminal window and running

```
sudo dpkg --configure -a
```

---

