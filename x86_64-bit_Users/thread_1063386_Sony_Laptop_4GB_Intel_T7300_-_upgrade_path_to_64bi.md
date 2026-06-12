---
title: "Sony Laptop 4GB Intel T7300 - upgrade path to 64bit"
date: 2009-02-07
forum: x86 64-bit Users
---

### Post by IQRules on 2009-02-07
@sony-laptop:~$ lspci | more
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controlle
r Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrat
ed Graphics Controller (rev 0c)

@sony-laptop:~$ cat /proc/mem*
MemTotal:      3102864 kB
MemFree:       2565432 kB
Buffers:         16016 kB

Is this normal on 32-bit 8.10 Ubuntu?

Is there a upgrade path to 64-bit w/o OS reload?

Thanks

---

### Post by Yellow Pasque on 2009-02-08
> Is this normal on 32-bit 8.10 Ubuntu?
Yes. A 32-bit OS can only access 3.2GB of RAM (not counting the RAM taken by the IGP) You either need a special 32-bit kernel with PAE (Physical Address Extension) to access all of your RAM or a reinstall with x86_64/amd64.

> Is there an upgrade path to 64-bit w/o OS reload?
No, but you should be able to re-use your /home directory if you wish.

---

### Post by IQRules on 2009-02-08
Here is the vga setup,

g@sony-laptop:~$ lspci -v -s 00:02.0
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
	Subsystem: Sony Corporation Device 9015
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fc000000 (64-bit, non-prefetchable) [size=1M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 1800 [size=8]
	Capabilities: <access denied>
	Kernel modules: intelfb

Does this mean, I just use 3102M + 256M here?

---

