---
title: "Extremely slow boot time"
date: 2008-02-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by pangel on 2008-02-29
I just completed a fresh install of Ubuntu on my laptop (dual boot with xp) and it takes about 3 minutes to boot past grub (while windows still boots in about 20 seconds).

I've put what seems problematic here: 
```
...

[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   18.292588] time.c: Detected 1794.871 MHz processor.

...

[   22.826581] ACPI: Thermal Zone [THRM] (0 C)
[   32.498045] usbcore: registered new interface driver usbfs

...

[   38.452563] EXT3-fs: mounted filesystem with ordered data mode.
[  126.366997] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

...

[  134.756114] EXT3 FS on hda2, internal journal
[  144.896909] ACPI: AC Adapter [ACAD] (on-line)

...

[  148.789690] powernow-k8: ph2 null fid transition 0xa
[  156.048278] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1

...

[  178.409850] eth0: no IPv6 routers present
[  179.551448] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  198.940130] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
```

and the bootchart there: **[http://tinyurl.com/2olop7](http://tinyurl.com/2olop7)**. 

Every search I made has led me to forums where the problem was network-related, and it seems like it is not the case for me.

I'm using a HP Pavilion dv5000 with an AMD Turion 64 Mobile.

---

### Post by hyperair on 2008-02-29
From your bootchart, it looks like an issue with readahead, though I could be wrong. Why don't you try profiling your boot and see if that helps?

---

### Post by pangel on 2008-02-29
I am not sure what you mean by profiling my boot so I put a complete bootlog here: [http://pastie.caboo.se/159532](http://pastie.caboo.se/159532)

Google also brought me to an obscure blog post by someone who had slow boot issues that were readahead-related. He said he added " profile" at the end of the ubuntu line in menu.lst. 

I couldn't find any other information about the options (ro, quiet, profile...) but I tried anyway, just in case that's what you were talking about. Unfortunately it did not change a thing.

---

### Post by fjgaude on 2008-02-29
You put the word "profile" after the boot line, re-boot, and then take it out. Is this what you did?

---

### Post by pangel on 2008-03-01
Yes, that's what I did - with no result. Here is the new bootchart and dmesg: [http://pastie.caboo.se/159691](http://pastie.caboo.se/159691)

I thought my problem was related to my use of the amd64 version of Ubuntu but I just switched to i386 and nothing changed, so maybe this thread should be moved somewhere else.

---

### Post by hyperair on 2008-03-01
Maybe I should create a bootchart of my own and compare. Hmm..

---

