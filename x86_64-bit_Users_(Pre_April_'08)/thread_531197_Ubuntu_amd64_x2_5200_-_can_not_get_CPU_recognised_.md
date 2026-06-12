---
title: "Ubuntu amd64 x2 5200 - can not get CPU recognised and no scaling possible"
date: 2007-08-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by nicolasdiogo on 2007-08-21
hi,

i am trying to enable CPU scaling on my desktop but my CPU does get detected properly with:
> dmesg | grep powernow

i have also uninstalled powernowd and tried to use powernow-k8 (COOL AND QUIET) but it also fails to load.

i am using a GA-M57SLI-S4 motherboard from giga-byte with their most recent BIOS update.

i would really appreciate some assistance here as i have run out of ideas and i am no expert in linux.

many thanks folks.


Nicolas


> dmesg | grep powernow
[   64.119000] powernow_k8: Unknown symbol acpi_processor_notify_smm
[   64.119031] powernow_k8: Unknown symbol acpi_processor_unregister_performance
[   64.119102] powernow_k8: Unknown symbol acpi_processor_register_performance
[28614.857206] powernow_k8: Unknown symbol acpi_processor_notify_smm
[28614.857239] powernow_k8: Unknown symbol acpi_processor_unregister_performance
[28614.857311] powernow_k8: Unknown symbol acpi_processor_register_performance
[30487.510787] powernow_k8: Unknown symbol acpi_processor_notify_smm
[30487.510820] powernow_k8: Unknown symbol acpi_processor_unregister_performance
[30487.510892] powernow_k8: Unknown symbol acpi_processor_register_performance
[30589.152203] powernow_k8: Unknown symbol acpi_processor_notify_smm
[30589.152236] powernow_k8: Unknown symbol acpi_processor_unregister_performance
[30589.152309] powernow_k8: Unknown symbol acpi_processor_register_performance
[30662.455513] powernow_k8: Unknown symbol acpi_processor_notify_smm
[30662.455546] powernow_k8: Unknown symbol acpi_processor_unregister_performance
[30662.455619] powernow_k8: Unknown symbol acpi_processor_register_performance
[31183.231210] powernow_k8: Unknown symbol acpi_processor_notify_smm
[31183.231244] powernow_k8: Unknown symbol acpi_processor_unregister_performance
[31183.231316] powernow_k8: Unknown symbol acpi_processor_register_performance


> cat /proc/cpuinfo
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 67
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
stepping	: 2
cpu MHz		: 2613.449
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8_legacy
bogomips	: 5233.91
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 67
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
stepping	: 2
cpu MHz		: 2613.449
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8_legacy
bogomips	: 5227.03
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

> modprobe powernow-k8
WARNING: Error inserting processor (/lib/modules/2.6.20-16-generic/kernel/drivers/acpi/processor.ko): No such device
FATAL: Error inserting powernow_k8 (/lib/modules/2.6.20-16-generic/kernel/arch/x86_64/kernel/cpufreq/powernow-k8.ko): Unknown symbol in module, or unknown parameter (see dmesg)

> dmesg

[32685.535076] powernow_k8: Unknown symbol acpi_processor_notify_smm
[32685.535109] powernow_k8: Unknown symbol acpi_processor_unregister_performance
[32685.535181] powernow_k8: Unknown symbol acpi_processor_register_performance

---

### Post by John.Michael.Kane on 2007-08-21
Please execute 'cpufreq-info' command and post output here.

---

### Post by nicolasdiogo on 2007-08-21
thanks for your assistance,

here it is:

> cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU

---

### Post by John.Michael.Kane on 2007-08-21
> **nicolasdiogo said:**
> thanks for your assistance,

here it is:

> cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU

The above error show for me when I uninstalled powernowd on the machine i'm using.

Try reinstalling powernowd.
```
gksudo aptitude install powernowd
```

Then rerun 
```
dmesg | grep powernow
```

And
```
cpufreq-info
```

Also check under your bios to make sure Cool'n'Quiet is enable.

---

### Post by nicolasdiogo on 2007-08-21
here it is:

> apt-get install powernowd

> /etc/init.d/powernowd start
 * Starting powernowd... 
/etc/init.d/powernowd: 156: cannot create /sys/devices/system/cpu/cpu0//cpufreq/scaling_governor: Directory nonexistent
 * CPU frequency scaling not supported
   ...done.
> dmesg | grep powernow
[   52.900873] powernow_k8: Unknown symbol acpi_processor_notify_smm
[   52.900905] powernow_k8: Unknown symbol acpi_processor_unregister_performance
[   52.900976] powernow_k8: Unknown symbol acpi_processor_register_performance
> cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU

what do you think?

---

### Post by John.Michael.Kane on 2007-08-21
> **nicolasdiogo said:**
> here it is:

> apt-get install powernowd

> /etc/init.d/powernowd start
 * Starting powernowd... 
/etc/init.d/powernowd: 156: cannot create /sys/devices/system/cpu/cpu0//cpufreq/scaling_governor: Directory nonexistent
 * CPU frequency scaling not supported
   ...done.
> dmesg | grep powernow
[   52.900873] powernow_k8: Unknown symbol acpi_processor_notify_smm
[   52.900905] powernow_k8: Unknown symbol acpi_processor_unregister_performance
[   52.900976] powernow_k8: Unknown symbol acpi_processor_register_performance
> cpufreq-info
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU

what do you think?

The errors lead me to feel theres a kernel issue with regard to your hardware.

With that said the processor certainly supports powerednow, and ubuntu has the support to adjust cpufreq. 

One other option. reinstall ubuntu using the command below.

Reboot the machine. At the boot/install prompt (make sure to hit F6 first), and add the command below to the boot parameter.
```
nosplash noapic nolapic
```  
note: do not remove any of the commands already shown in the boot line. just add the above commands to it.

---

### Post by nicolasdiogo on 2007-08-21
so you think i should reinstall using those commands that you listed above.
i am happy to do that.
but for the record i have installed using:

acpi=off

any idea on why that has happened?

many thanks

---

### Post by stmiller on 2007-08-21
Do you know if that bios supports that CPU? Email the motherboard tech support if possible, to ask and find out.

---

### Post by nicolasdiogo on 2007-08-21
i have checked the manufactured and asked it they know of other people having issues and they claim that i am the first to ask such a question.
the motherboard supports X2 amd64 am2 CPU.

thus mine is supported.

thanks

---

### Post by stmiller on 2007-08-22
> **nicolasdiogo said:**
> i have checked the manufactured and asked it they know of other people having issues and they claim that i am the first to ask such a question.
the motherboard supports X2 amd64 am2 CPU.

thus mine is supported.

thanks

Just because it fits the socket does not mean the BIOS supports that chip. My X2 3600 required a BIOS update when it was hot off the press from AMD last year. Even though my motherboard was AM2, it still required a BIOS update. I had similar problems that you are experiencing.

---

### Post by nicolasdiogo on 2007-08-22
i have checked gigabyte website and the CPU is supported by the motherboard, and i have also update the BIOS to the most recent.

[http://www.gigabyte.com.tw/Support/Motherboard/CPUSupport_Model.aspx?ClassValue=Motherboard&ProductID=2287&ProductName=GA-M57SLI-S4](http://www.gigabyte.com.tw/Support/Motherboard/CPUSupport_Model.aspx?ClassValue=Motherboard&ProductID=2287&ProductName=GA-M57SLI-S4)


i tried to install the system with the above kernel parameters and it installs but does not boot up, thus i tried with my previous option (acpi=off) and it did not start.

it is getting worse, but i will reinstall it and let you know of result.

thanks for your assistance

---

### Post by nicolasdiogo on 2007-08-22
i reinstalled using acpi=off.
there is no cpu frequency support.

since i had a cd with gutsy near by i loaded it and for my surprise it identifies my cpu perfectly. i even get the gnome applets to work.

thus i do not think i will have any luck in getting feisty to give cpu scaling and maybe i should wait for gutsy to be released.

i was testing opensuse 10.2 and cpu as well as rest of hardware is detect and supported.

any comments?


thanks

---

### Post by kipman725 on 2007-08-22
On my motherboard cool'n quite only works with ACPI enabled which is quite annoying as it's ACPI is totaly messed up and will only work with windows.

---

### Post by nicolasdiogo on 2007-08-26
> **SD-Plissken said:**
> 
Reboot the machine. At the boot/install prompt (make sure to hit F6 first), and add the command below to the boot parameter.
```
nosplash noapic nolapic
```  
note: do not remove any of the commands already shown in the boot line. just add the above commands to it.

many thanks for your suggestions.

but it seems to be a problem with the kernel curretly provided with feisty:

2.6.20-16-generic

it does not recognise the CPU no matter what boot parameters i used.

to enable CPU scaling i have installed GUTSY kernel

2.6.22-10-generic

so far it is working fine.

i have utilized the instruction provided here:

[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

Hope it helps some..

regads,

nicolas

---

