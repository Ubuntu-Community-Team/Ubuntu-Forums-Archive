---
title: "Laptop fan control"
date: 2006-06-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by Markiedam on 2006-06-15
Hi,

I have a Acer Aspire 5024WLMi running Dapper Draker 6.06 (final).
I am using kernel linux-image-k7 (so i am using the 32 bit version of ubuntu).
My problem is that the fans in my laptop consitanly are blowing. The frequency
scaling feature works fine. He switches nicely between 800Mhz and 1.8Ghz.

How can i make my laptop quiet again?

```

dr-xr-xr-x 3 root root 0 2006-06-15 14:49 ac_adapter
-rw-r--r-- 1 root root 0 2006-06-15 14:49 alarm
dr-xr-xr-x 3 root root 0 2006-06-15 14:49 battery
dr-xr-xr-x 5 root root 0 2006-06-15 14:49 button
-r-------- 1 root root 0 2006-06-15 14:49 dsdt
dr-xr-xr-x 3 root root 0 2006-06-15 14:49 embedded_controller
-r-------- 1 root root 0 2006-06-15 14:46 event
-r-------- 1 root root 0 2006-06-15 14:49 fadt
dr-xr-xr-x 2 root root 0 2006-06-15 14:48 fan
dr-xr-xr-x 2 root root 0 2006-06-15 14:49 hotkey
-r--r--r-- 1 root root 0 2006-06-15 14:49 info
-rw------- 1 root root 0 2006-06-15 14:49 poolsize
dr-xr-xr-x 2 root root 0 2006-06-15 14:49 power_resource
dr-xr-xr-x 3 root root 0 2006-06-15 14:49 processor
dr-xr-xr-x 2 root root 0 2006-06-15 14:49 sbs
-rw-r--r-- 1 root root 0 2006-06-15 14:49 sleep
dr-xr-xr-x 2 root root 0 2006-06-15 14:49 sony
dr-xr-xr-x 5 root root 0 2006-06-15 14:49 thermal_zone
dr-xr-xr-x 4 root root 0 2006-06-15 14:49 video
-rw-r--r-- 1 root root 0 2006-06-15 14:49 wakeup
dr-xr-xr-x 2 root root 0 2006-06-15 14:49 wmi
markiedam@markiedam-ubuntu:/proc/acpi$ ls -l fan/
total 0

```

---

### Post by henriquemaia on 2006-06-15
Try reading this thread, maybe this will help out:

[http://ubuntuforums.org/showthread.php?t=42737&highlight=fan+speed+control]("http://ubuntuforums.org/showthread.php?t=42737&highlight=fan+speed+control")

---

### Post by Markiedam on 2006-06-15
[QUOTE=henriquemaia]Try reading this thread, maybe this will help out:

[http://ubuntuforums.org/showthread.php?t=42737&highlight=fan+speed+control]("http://ubuntuforums.org/showthread.php?t=42737&highlight=fan+speed+control")[/QUOTE]
Sadly enough lm-sensors is not supported by my chipset (ATI SMBus)

---

