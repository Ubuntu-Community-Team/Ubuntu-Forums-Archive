---
title: "boot manager and loader"
date: 2005-04-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by rjz on 2005-04-17
What 3rd part boot manager and loader do you recomend for ubuntu linux and windows xp 64? I would like to be able to select from a list. Also I would like to try other linux versions later as well. Is there an easy way to do this?

---

### Post by soul_rebel on 2005-04-18
why would you need a third party boot loader? grub can boot almost anything!

---

### Post by rjz on 2005-04-18
Win XP 64 is now on and it will not load in grub. I had to load it in the mbr. Is there now a way to load grub or another loader in the mbr?

---

### Post by soul_rebel on 2005-04-18
yes you can install grub again in the mbr, overwriting windows ntloader. I think i'd start with
```
man grub-install
```

bye

---

