---
title: "Turion 64 X2 second core offline"
date: 2007-05-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by pacadi on 2007-05-07
Hi:
Just installed 7.04 AMD64 on an HP DV2000 laptop (Turion 64 X2). Everything installed just fine. One thing that irritates me though is that it seems that the second CPU core is offline after boot. When I "cat /proc/interrupts", I basically see "0" interrupts on cpu1. cpu0 seems just steadily incrementing interrupts. The system is running an SMP kernel, that's at least what "uname -a" says. Any ideas anyone?

BTW, I also booted the 6.10 AMD64 life CD, and it has the same problem...

Thanks for any help,

Patrick

---

### Post by ronacc on 2007-05-08
I have athalon x2's running 7.04 on 2 desktops , both cores share the load just fine on those , Ubuntu likes the amd x2's so I don't think the problem is there.Check your power management settings , does that HP mabye put one core to sleep when its not needed ?

---

### Post by pacadi on 2007-05-08
Hi! Thanks for the reply... I will check the power management settings and post again. The weird thing is that an openSuse 10.2 installation on the same machine boots up fine with both cores active. So it would really need to be Ubuntu that disables (or not enables) the second core.

(BTW, Suse has a different issue... it clearly does not bring the second core back online after resuming from hibernate...)

Patrick

---

### Post by pacadi on 2007-05-08
OK, here some more data:
as far as I can tell power management settings should be OK. I did not see anything that would suggest that the second core would be disabled.

[FONT="Courier New"]#cat /sys/devices/system/cpu/cpu1/online
1
# cat /proc/interrupts
           CPU0       CPU1
  0:    1924896       0   IO-APIC-edge      timer
  1:       1734          0   IO-APIC-edge      i8042
  8:          0             0   IO-APIC-edge      rtc
  9:      24066         0   IO-APIC-fasteoi   acpi
 12:      52465        0   IO-APIC-edge      i8042
 15:      67991        0   IO-APIC-edge      ide1
 17:      17659        0   IO-APIC-fasteoi   HDA Intel
 18:          0            0   IO-APIC-fasteoi   sdhci:slot0
 19:     785072       0   IO-APIC-fasteoi   eth0
 20:    1524386      0   IO-APIC-fasteoi   ohci_hcd:usb2
 21:          4            0   IO-APIC-fasteoi   ohci1394
 22:         23           0   IO-APIC-fasteoi   ehci_hcd:usb1
 23:      25559        0   IO-APIC-fasteoi   libata
NMI:          0           0
LOC:    1873844    1864712
ERR:          0[/FONT]

I also installed the sysstat package and used mpstat to get some info:
#mpstat
Linux 2.6.20-15-generic (nq2x)  05/08/2007

12:21:55 PM  CPU   %user   %nice    %sys %iowait    %irq   %soft  %steal   %idle    intr/s
12:21:55 PM  all    0.32    0.00    0.12    0.55    0.13    0.01    0.00   98.88    587.30

That's the weirdest thing to begin with: on SMP systems the output format should be like:
CPU
all
0
1

So, for mpstat there is no second core...:confused: 

Just weird...

---

### Post by ronacc on 2007-05-09
try booting with the noapic boot option, when grub comes up press e  to edit the boot paramaters add noapic and  press b to continue the boot , also you could try adding noacpi and then adding both. if one of those works add it to your boot args in /boot/grub/menu.lst  .

---

