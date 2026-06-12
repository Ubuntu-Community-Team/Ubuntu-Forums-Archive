---
title: "Monitor in 64 vs. 32 bit Edgy"
date: 2006-12-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by Negative_3 on 2006-12-25
My desktop has an ATI x800 Pro with a Dell Trinitron monitor hooked up to it.

In 32-Bit Edgy, it lets me go up to 1600x1200 at 85 htz from the live CD.  In 64-Bit Edgy it only lets me go up to 1024x768 at 60 htz from the live CD.  What gives?

---

### Post by pay on 2006-12-25
What driver are you doing this with? The default driver? Or the fglrx driver?

---

### Post by Negative_3 on 2006-12-25
Uh... I'm not sure.  How do I find out?

---

### Post by pay on 2006-12-25
```
cat /etc/X11/xorg.conf
```and post the results. You might find that you have better video with the fglrx driver, at expense of freedom...

---

