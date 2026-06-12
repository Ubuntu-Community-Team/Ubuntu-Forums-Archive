---
title: "Problem compiling acer_acpi..."
date: 2005-12-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by bnewman on 2005-12-27
Hi all, I am trying to get my wireless working under breezy and have had no luck thus far. I have an acer aspire 5000; I have ndiswrapper installed, as well as the driver for my card. From what I understand, I need either acerhk or acer_a```

```cpi to activate the LED on my card. From what I've read, this is necessary to connect to a wireless AP. When I issue "make" in the directory for acer_acpi, I end up getting...

```
make[2]: *** [/home/bnewman/Desktop/acer_acpi-0.3/acer_acpi.o] Error 1
make[1]: *** [_module_/home/bnewman/Desktop/acer_acpi-0.3] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-amd64-generic'
make: *** [acer_acpi.ko] Error 2
```

I end up getting the same thing for acerhk. I'm a complete newbie, so if you have a solution, a little explanation would be much appreciated, just so I can learn my way around a little quicker. Thanks in advance.

---

### Post by dissdigg on 2005-12-31
I'm having the same problem.

---

### Post by Suger on 2006-01-01
We need a few lines before the one you give to help you

---

### Post by redsmoke on 2006-01-01
You do not need ACPI to get your wifi working as far as I know I have an acer aspire 5002 and I got wifi working long before I figured out how to get ACPI working properly...

Try this tutorial on getting ACPI working: [https://wiki.ubuntu.com/ACPIBattery?highlight=%28acpi%29](https://wiki.ubuntu.com/ACPIBattery?highlight=%28acpi%29)

And this thread should get your wifi working: [http://ubuntuforums.org/showthread.php?t=110749](http://ubuntuforums.org/showthread.php?t=110749)

Be sure to install build-essentials ( sudo apt-get install build-essentials ) before attempting the wifi one.

---

