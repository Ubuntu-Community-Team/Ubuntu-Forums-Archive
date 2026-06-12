---
title: "Unknown Hardware"
date: 2006-04-28
forum: x86 64-bit Users (Pre April '08)
---

### Post by Prasad007 on 2006-04-28
The device manager detects most of the hardware as unknown.
All my drivers cd's dont run on linux theyre for windows.
wat can be done?

---

### Post by linuxfanatic1024 on 2006-04-28
Can you please paste the output of this command here:

```
lspci
```

That will help for sure.

---

### Post by Unen on 2006-04-29
im also having the same problem... where do i enter this code "lspci"?

---

### Post by Prasad007 on 2006-04-29
how can i "output" it? where do i type it?
is there a console or something?


new to linux... first timer...

---

### Post by Prasad007 on 2006-04-29
okay did it thru terminal
output :
0000:00:00.0 Memory controller: nVidia Corporation: Unknown device 005e (rev a3)0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 0050 (rev a3)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 0052 (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 005a (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 005b (rev a3)
0000:00:04.0 Multimedia audio controller: nVidia Corporation: Unknown device 0059 (rev a2)
0000:00:06.0 IDE interface: nVidia Corporation: Unknown device 0053 (rev a2)
0000:00:07.0 IDE interface: nVidia Corporation: Unknown device 0054 (rev a3)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 0055 (rev a3)
0000:00:09.0 PCI bridge: nVidia Corporation: Unknown device 005c (rev a2)
0000:00:0a.0 Bridge: nVidia Corporation: Unknown device 0057 (rev a3)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0c.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0d.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 005d (rev a3)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:07.0 Modem: Smart Link Ltd.: Unknown device 8800 (rev 02)
0000:01:0b.0 FireWire (IEEE 1394): Lucent Microelectronics FW323 (rev 61)
0000:05:00.0 VGA compatible controller: nVidia Corporation: Unknown device 00c0 (rev a2)

---

### Post by Unen on 2006-04-29
scratch that... the console is under Applications > Accessories > Terminal
i lspci'd there and got a bunch of returns for my hardware devices... such as my sound, gfx, networking card etc. linux is picking them up, but i guess theres a problem with drivers

---

### Post by huckem on 2006-04-30
I am having the same issue... It seems like even after I install the Nvidia drivers (the chipset ones, not the video ones) I dont get any sensible output in device manager.  I am using a KN8 SLi mobo and a Opty 170 proc, Nforce 4 chipset.  Anyone know the solution to this?

---

