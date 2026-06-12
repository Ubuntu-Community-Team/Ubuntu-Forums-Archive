---
title: "Battery not recognised in Intrepid"
date: 2009-02-12
forum: x86 64-bit Users
---

### Post by borobudur on 2009-02-12
Hi, I installed Ubuntu Intrepid 8.10 on my AMD64 Laptop. The battery isn't recognised. 

With Ubuntu 6.10 I had to add an additional attribute in the grub file: nohpet

With Ubuntu 7.10 it wasn't necessary anymore. Now with 8.10 both won't enable my battery in the OS.

Can somebody help me please?

---

### Post by borobudur on 2009-02-27
*** bump ***

---

### Post by stchman on 2009-02-27
What do you mean?  When you unplug the laptop AC does the laptop still remain powered.

---

### Post by Yellow Pasque on 2009-02-27
What model laptop?

---

### Post by borobudur on 2009-02-28
It's a MSI Megabook S271 with a AMD 64 bit CPU.

The battery icon stays always there empty in the Gnome panel. The laptop gets power from the battery but the system (Intrepid) doesn't recognize it.

---

### Post by borobudur on 2009-03-16
Anybody, please help!

---

### Post by novafluxx on 2009-03-16
Do you have a dual boot system? Have you tried seeing if Windows recognizes it?

Have you/Can you check your BIOS to see if the battery is recognized properly in the BIOS?

I know with Dell systems you can check the adapter and battery in the BIOS.

---

### Post by borobudur on 2009-03-17
I will check the Bios but I don't think it's this. I had battery support before and it just appeared with the new installation of Interpid.

---

### Post by borobudur on 2009-03-28
Played around with the bios options but no success. Does these information someone help?
```
user@machine:~$ cat /proc/acpi/battery/BAT1/state 
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            unknown
remaining capacity:      unknown
present voltage:         10000 mV
``````
user@machine:~$ sudo lsmod
Module                  Size  Used by
ac                     13448  0 
battery                21128  0 
button                 15904  0 
thermal                27424  0 
processor              47800  2 powernow_k8,thermal
fan                    13576  0 
...
``````
user@machine:~$ acpi -b
     Battery 0: Full, 100%
``````
user@machine:~$ acpi -a
     Battery 0: Full, 100%
  AC Adapter 0: on-line
```
Tried also adding **acpi=force** to the kernel line and the kernel option **acpi_osi="Linux"** in /boot/grub/menu.lst

What's the problem here :confused:

---

