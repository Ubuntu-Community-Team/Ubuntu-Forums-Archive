---
title: "ibook g4 + external TFT monitor"
date: 2005-12-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by pallus on 2005-12-05
Hi, i have an ibook g4 with Ubuntu 5.10. I need to connect an external TFT monitor i order to get more workable environement, but when i connect the monitor to the laptop throught the DVI-VGA adapter nothing happens. The external TFT monitor remains without signal.
 is there any way to get it work?

Thank you in advance!
Manel

---

### Post by ssam on 2005-12-05
with an iBook you will only be able to mirror the main display.

have a look through

```
man radeon
```
or
```
man nv
```

to find the relivent xorg.conf options (if its possible.)

---

### Post by hentaidan on 2005-12-05
I was under the impression that the graphics card in iBook G4's were not supported; or is this only the newer models?

---

