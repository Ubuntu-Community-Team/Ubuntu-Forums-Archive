---
title: "Catalyst 9.4 overdrive - anyone using it?"
date: 2009-04-21
forum: x86 64-bit Users
---

### Post by blacksm1th on 2009-04-21
Hi, I have strange problem with Ati Overdrive in both Jaunty/Intrepid. Anyone using overdrive feature in Ubuntu? Here is the situation:
1. Ihave this configuration:
```
====================================
Phoronix Test Suite v1.8.1 (SELBU)
System Information
====================================

Hardware:
Processor: AMD Sempron 3000+ @ 1.80GHz (Total Cores: 1), Motherboard: K8NF4G-SATA2., Chipset: nVidia C51, System Memory: 2008MB, 
Disk: 640GB SAMSUNG HD642JJ, Graphics: ATI Radeon HD 3600 Series 512MB (300/400MHz), Monitor: W1934

Software:
OS: Ubuntu 8.10, Kernel: 2.6.27-11-generic (x86_64), Desktop: GNOME 2.24.1, Display Server: X.Org Server 1.5.2, 
Display Driver: fglrx 8.60.3, OpenGL: 2.1.8591, Compiler: GCC 4.3.2, File-System: ext3, Screen Resolution: 1440x900
```
2. The default frequency of GPU in 3D mode is 725MHz but:
```
$ aticonfig --od-getclocks
Default Adapter - ATI Radeon HD 3600 Series
                            Core (MHz)    Memory (MHz)
           Current Clocks :    300           400
             Current Peak :    300           400
  Configurable Peak Range : [300-900]     [400-700]
                 GPU load :    1%
```
Current Peak must be 725MHz

3. When i try to set it manually:
```
$ aticonfig --od-setclocks=725,400
ERROR - Set clocks failed for Default Adapter - ATI Radeon HD 3600 Series
        Please check that input values were valid
```
4. It worked before but now even with fresh Intrepid install (with or without all updates) and older Catalyst 9.2 it wouldn't.

5.If anyone can confirm status of aticonfig --od-setclocks please tell us.

---

