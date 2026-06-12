---
title: "Give Process Higher Priority"
date: 2008-12-14
forum: x86 64-bit Users
---

### Post by benzidirk on 2008-12-14
Hi.. Quick question.. how can a give to a process higher priority.. how can i do that?
thanks.

---

### Post by stoneage on 2008-12-14
You can do that with System Monitor. It is available as a panel applet. Right click on panel, choose Add to Panel and scroll down to System Monitor. Open System Monitor, choose Processes tab, right click on process and choose Change Priority.

---

### Post by Ng Oon-Ee on 2008-12-14
Just a note, i don't think you can increase the priority without root priveledges by default. That was my experience previously, however I don't have any current knowledge so this may have changed.

Oh, and priority is inverted, lower numbers are better.

---

### Post by Bear Knuckle on 2008-12-15
For new processes:
```
man nice
```
For running processes:
```
man renice
```

---

