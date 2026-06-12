---
title: "CPU temp monitoring on Powerbook?"
date: 2006-04-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by Entity on 2006-04-16
I have a Powerbook on which I would like to be able to monitor the CPU temp. So I installed lm-sensors, ran sensors-detect but no luck...

$ cat /proc/cpuinfo
processor       : 0
cpu             : 7447A, altivec supported
clock           : 749.999000MHz
revision        : 0.1 (pvr 8003 0101)
bogomips        : 36.73
timebase        : 18432000
machine         : PowerBook5,5
motherboard     : PowerBook5,5 MacRISC3 Power Macintosh
detected as     : 287 (PowerBook G4 17")
pmac flags      : 0000001b
L2 cache        : 512K unified
pmac-generation : NewWorld

Any ideas on how I could get this done?

---

### Post by dpny on 2006-04-16
From what I've been able to tell, lm-sensors is not yet able to monitor a Powerbook's temp. I have asked this question before, with no luck.

---

### Post by callipeo on 2006-04-17
Maybe you can try with Laptop Temperature Monitor: [http://laptoptemp.berlios.de/](http://laptoptemp.berlios.de/)

---

### Post by Entity on 2006-04-17
[QUOTE=callipeo]Maybe you can try with Laptop Temperature Monitor: [http://laptoptemp.berlios.de/](http://laptoptemp.berlios.de/)[/QUOTE]

Damn, it works! It seems to be using the therm_adt746x module in order to give CPU/GPU temp ;-)

---

### Post by dpny on 2006-04-17
Tried to comple the source and got this error:

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for python... /usr/bin/python
checking for python version... 2.4
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.4/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.4/site-packages
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PYGTK... configure: error: Package requirements (pygtk-2.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.
```

Synaptic tells me pygtk is installed and at version 2.8.1.

---

### Post by Entity on 2006-04-18
[QUOTE=dpny]Tried to comple the source and got this error:

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for python... /usr/bin/python
checking for python version... 2.4
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.4/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.4/site-packages
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PYGTK... configure: error: Package requirements (pygtk-2.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.
```

Synaptic tells me pygtk is installed and at version 2.8.1.[/QUOTE]
Why don't you directly install the binary?

[Dapper]("http://download.berlios.de/laptoptemp/laptoptemp_0.8.0-0ubuntu1_all_dapper.deb") or [Breezy]("http://download.berlios.de/laptoptemp/laptoptemp_0.8.0-0ubuntu1_all_breezy.deb")

---

### Post by dpny on 2006-04-18
[QUOTE=Entity]Why don't you directly install the binary?

[Dapper]("http://download.berlios.de/laptoptemp/laptoptemp_0.8.0-0ubuntu1_all_dapper.deb") or [Breezy]("http://download.berlios.de/laptoptemp/laptoptemp_0.8.0-0ubuntu1_all_breezy.deb")[/QUOTE]

Installed the breezy package, installed lm-sensors and when I try to add the app to my panel I get the message "There is not Thermal Monitor support on your machine:.

---

### Post by callipeo on 2006-04-19
[QUOTE=dpny]Installed the breezy package, installed lm-sensors and when I try to add the app to my panel I get the message "There is not Thermal Monitor support on your machine:.[/QUOTE]

lm-sensors should not be required to run the applet. On what machine do you run it?  Do you have the therm_adt746x module loaded (you can check it with "lsmod | grep therm_adt746x")? Do you have the /sys/devices/temperatures/ directory?

---

### Post by dpny on 2006-04-19
[QUOTE=callipeo]lm-sensors should not be required to run the applet. On what machine do you run it?  Do you have the therm_adt746x module loaded (you can check it with "lsmod | grep therm_adt746x")? Do you have the /sys/devices/temperatures/ directory?[/QUOTE]

I'm running it on a 500 MHz Powerbook with a 900 MHz cpu upgrade card. I don't have the therm_adt746x module. I tried putting it in /etc/modules, but it didn't load. And I have no /sys/devices/temperatures/ directory.

---

### Post by callipeo on 2006-04-20
[QUOTE=dpny]I'm running it on a 500 MHz Powerbook with a 900 MHz cpu upgrade card. I don't have the therm_adt746x module. I tried putting it in /etc/modules, but it didn't load. And I have no /sys/devices/temperatures/ directory.[/QUOTE]

The applet use the interface provided by the therm_adt746x module, so if you haven't it on your system you have actually little hope to get it working :-(. If you know of any other method to know the cpu temperature on your machine on a particular instant, maybe someone could add a module to laptoptemp (i could probably write it, provided that I have enough information).

---

### Post by dpny on 2006-04-20
[QUOTE=callipeo]The applet use the interface provided by the therm_adt746x module, so if you haven't it on your system you have actually little hope to get it working :-(. If you know of any other method to know the cpu temperature on your machine on a particular instant, maybe someone could add a module to laptoptemp (i could probably write it, provided that I have enough information).[/QUOTE]

Can I add it to my system? Download? Compile?

---

