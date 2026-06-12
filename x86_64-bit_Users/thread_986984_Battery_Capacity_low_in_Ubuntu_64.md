---
title: "Battery Capacity low in Ubuntu 64"
date: 2008-11-19
forum: x86 64-bit Users
---

### Post by RonenIL on 2008-11-19
hello,
i'm a new user of ubuntu.(1 week).
when i installed the ubuntu 8.10 64 bit i had a note that my battery is maybe broken and the capacity is 65%.
i think that's cannot be because my laptop HP DV5-1000US  is 1 month old 
windows doesnt say anything about my battery and the battery is going very low quickly in ubuntu . 

can i do something about it ?

thanx for the help.

---

### Post by prshah on 2008-11-19
> **RonenIL said:**
> 
when i installed the ubuntu 8.10 64 bit i had a note that my battery is maybe broken and the capacity is 65%.
i think that's cannot be because my laptop HP DV5-1000US  is 1 month old 
windows doesnt say anything about my battery and the battery is going very low quickly in ubuntu .

Windows does not have the programming for battery monitoring. This feature is only available in Linux.

However, it is very likely that the warning is false, since this feature is not foolproof.

Normally, linux does cause a higher battery usage in most laptops (this is due to faulty or absent acpi implementation for linux).

How does the battery life behave in Windows? Do you get proper battery life (at least 80% of manufacturer specs / claims)? Otherwise, Linux may well be warning you of a possible and impending battery failure.

You can try 2 charge / discharge cycles; use your notebook until battery totally drains out, then charge it up fully, and repeat the process. Does Linux still give you battery warnings?

---

### Post by RonenIL on 2008-11-19
i'll try to do it in this days , and i'll keep u posted

---

### Post by Svenstaro on 2008-11-19
Install "powertop" and see if there's something that wakes your kernel very often. You should aim for something below 100 times a second. If it is much higher in idle there's definately something wrong. Also check the output of "cat /proc/acpi/battery/BAT*/state" and "cat /proc/acpi/battery/BAT*/info".

---

### Post by juanfer2k on 2009-01-25
I think i vahe the same issue of the battery, also, i have been advised to do the charging ciclying method, just they toldme to charge once with the computer off.

---

