---
title: "Edgy not recognizing my Ethernet chip"
date: 2006-11-11
forum: x86 64-bit Users (Pre April '08)
---

### Post by Zed on 2006-11-11
I just installed Edgy AMD64 on an Asrock Conroe945G-DVI with an E6400 (Core 2 Duo.) Though the machine is attached to my router, and my Windows XP installation on the same drive can access the Net, the Edgy installation didn't recognize any network hardware. The Ethernet chip is a Realtek rtl8111b.

lspci -v says:

```

01:00.0 Ethernet controller: Realtek Semiconductor Co., Lcd. Unknown device 8168 (rev 01)
  Subsystem: Asrock Incorporation Unknown device 8168
  Flags: bus master, fast devsel, latency 0, IRQ 177
  I/O ports at e800 [size=256]
  Memory at febff000 (64-bit, non-prefetchable) [size=4K]
  Expansion ROM at febc0000 [disabled] [size=128K]
  Capabilities: [40] Power Management version 2
  Capabilities: [48] Vital Product Data
  Capabilities: [50] Message signalled Interrepts: 64bit+Queue=0/1 Enable_
  Capabilities: [60] Express End point IRQ 0
  Capabilities: [84] Vendor Specific Information

```

lsmod indicates I do have the r1000 module loaded.

Any advice? (I'm posting this from Windows. Oh, the ignominy!)

---

### Post by Zed on 2006-11-11
Solved it by building my own based on the info [here.](http://forums.suselinuxsupport.de/index.php?showtopic=36365&pid=198303&st=40&#entry198303)

---

### Post by beastly on 2006-11-22
Thanks for that, worked a treat on my x86_64 Edgy system!

---

