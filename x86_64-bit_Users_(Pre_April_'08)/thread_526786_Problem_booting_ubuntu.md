---
title: "Problem booting ubuntu"
date: 2007-08-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by ceriium on 2007-08-15
Ok, I originally used the regular CD and it wouldn't get past the loading splash screen.  I just used the alternate CD and it installed fine in text mode, but when i boot to ubuntu it just goes to a black screen and nothing happens.

pls help!


_System_
Intel E6300
4gb Corsair XM2
Nvidia 8800GTS using **DVI**
Seagate 160hd

---

### Post by ceriium on 2007-08-15
ok i deleted "splash" in the kernal line and it booted in text, but it after the first 5 tings load "OK" it gets stuck  on "Loading Hardware drivers"

---

### Post by John.Michael.Kane on 2007-08-16
> **ceriium said:**
> ok i deleted "splash" in the kernal line and it booted in text, but it after the first 5 tings load "OK" it gets stuck  on "Loading Hardware drivers"

Try rebooting the machine. At the boot/install prompt (make sure to hit F6 first), and add the command below to the boot parameter.
```
nosplash noapic nolapic
```  
note: do not remove any of the commands already shown in the boot line. just add the above commands to it.

---

### Post by leathco on 2007-08-16
> **SD-Plissken said:**
> Try rebooting the machine. At the boot/install prompt (make sure to hit F6 first), and add the command below to the boot parameter.
```
nosplash noapic nolapic
```  
note: do not remove any of the commands already shown in the boot line. just add the above commands to it.

OK keep in mind I'm a total n00b at the Linux and Ubuntu world, but I'm so frustrated with Vista I figured it was the perfect time to switch.

My installer kept locking up as well, I saw this post, tried these commands, and now I am installing via the 64 bit Live DVD fine.  What exactly do these commands do?

PS my system is a HP Pavilion dv6227cl.  Specs are below.

HP Pavilion dv6227cl Laptop PC - AMD Turion 64 X2 Dual-Core TL-50 1.6GHz, 802.11b/g Wireless, 2GB DDR2, 120GB HDD, Dual Layer DVD RW, 15.4" WXGA.

---

### Post by John.Michael.Kane on 2007-08-16
> **leathco said:**
> OK keep in mind I'm a total n00b at the Linux and Ubuntu world, but I'm so frustrated with Vista I figured it was the perfect time to switch.

My installer kept locking up as well, I saw this post, tried these commands, and now I am installing via the 64 bit Live DVD fine.  What exactly do these commands do?

PS my system is a HP Pavilion dv6227cl.  Specs are below.

HP Pavilion dv6227cl Laptop PC - AMD Turion 64 X2 Dual-Core TL-50 1.6GHz, 802.11b/g Wireless, 2GB DDR2, 120GB HDD, Dual Layer DVD RW, 15.4" WXGA.

```
Option: nosplash

Impact: Disable the "Graphical Boot Process" 

Option: noapic

Impact: Disable the "Advanced Programmable Interrupt Controller (APIC)".

Option: nolapic

Impact: Disable the "local APIC". 
```

---

### Post by ceriium on 2007-08-16
> **SD-Plissken said:**
> Try rebooting the machine. At the boot/install prompt (make sure to hit F6 first), and add the command below to the boot parameter.
```
nosplash noapic nolapic
```  
note: do not remove any of the commands already shown in the boot line. just add the above commands to it.

still having same problem

---

### Post by six on 2007-08-16
Try just removing the **quiet** and the **splash** in the kernel parameters, without  adding the 'no' ones.

---

### Post by backstrap on 2007-08-16
this may be a little moot at this point but i had the same problem with an HP 6105us laptop... specs below

AMD Turion 64 X2 52
512 generic 533 ram
80 drive
Nvidia 6150 up to 512 shared... meh machine...


from the booted cd i hit f6

and the boot line appeared..
...........[forgot the exact line]....... quiet splash--
all i did was change the line thus

............[sorry for not remembering] quiet [delete spash] nosplash noapic nolapic 

and it worked perfect. this may be my newness to ubuntu and linux in general but my install spazzed when both splash and nosplash were present.

sorry if im just stating the obvious. 


-Backstrap:

---

