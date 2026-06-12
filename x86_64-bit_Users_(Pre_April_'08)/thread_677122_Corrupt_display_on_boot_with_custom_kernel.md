---
title: "Corrupt display on boot with custom kernel"
date: 2008-01-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by Philio on 2008-01-24
I have just compiled a custom kernel, I made the following changes (using default .config file).

Patched for dmraid RAID 5 support (and enabled option in config)
Changed CPU type to Intel
Changed to SLAB for X-Fi compatibility

The kernel works fine but for some reason the bootup screen is corrupt, I've tried different display modes to no avail.

Does anyone know what might be causing the framebuffer to show a corrupt display?

---

### Post by Philio on 2008-01-24
Solved problem, well not solved as such but rebuilt kernel using Ubuntu sources (rather than kernel.org sources) and no longer have any issues with framebuffer :guitar:

---

