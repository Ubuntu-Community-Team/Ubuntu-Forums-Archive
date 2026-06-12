---
title: "[SOLVED] Frequency scaling unsupported"
date: 2008-06-01
forum: x86 64-bit Users
---

### Post by TouchuvGrey on 2008-06-01
HP laptop running 8.04 Hardy. "Frequency scaling Unsupported"

---

### Post by kingtaurus on 2008-06-02
Can you post the specs of the laptop? Without them we can't decide whether its the laptop or the kernel.

---

### Post by TouchuvGrey on 2008-06-09
HP Pavillion dv8000 laptop with an AMD Turion64.

frequency scaling worked fine in 7.04. Sorry for
the delay in replying, i was on vacation.

---

### Post by cubeist on 2008-06-09
> **TouchuvGrey said:**
> HP Pavillion dv8000 laptop with an AMD Turion64.

frequency scaling worked fine in 7.04. Sorry for
the delay in replying, i was on vacation.
```

sudo apt-get install powernowd
```

then
```

sudo modprobe powernow-k8
```

If that doesn't work, try 

```
sudo dpkg-reconfigure gnome-applets
```

---

