---
title: "kernel qustion for amd"
date: 2006-03-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by pestypest on 2006-03-15
ok question is, is there a kernel for amd Dual core chips?

---

### Post by Sutekh on 2006-03-15
Absolutely.

```
sudo apt-get install linux-amd64-k8-smp
```

Will get you the latest AMD64-K8-SMP kernel.  Once it is installed, it should update the GRUB menu, and when you reboot you should have the option of booting with the default kernel of the new SMP kernel.

To check that things are working correctly, use this code
```
cat /proc/cpuinfo
```
You should have two entries, one for each processor (processor 0, processor 1)

---

### Post by pestypest on 2006-03-15
[QUOTE=Sutekh]Absolutely.

```
sudo apt-get install linux-amd64-k8-smp
```

Will get you the latest AMD64-K8-SMP kernel.  Once it is installed, it should update the GRUB menu, and when you reboot you should have the option of booting with the default kernel of the new SMP kernel.

To check that things are working correctly, use this code
```
cat /proc/cpuinfo
```
You should have two entries, one for each processor (processor 0, processor 1)[/QUOTE]
Sweet thanks downloading and ill let u know how it goes after i get everything going.

---

