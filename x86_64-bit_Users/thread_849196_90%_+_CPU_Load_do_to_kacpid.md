---
title: "90% + CPU Load do to kacpid"
date: 2008-07-04
forum: x86 64-bit Users
---

### Post by Midgett on 2008-07-04
Hello everyone

i was wondering if anyone else had this problem. my cpu load is 93% or higher at idle and i couldnt figure out what was causing it till i checked the "top" in the terminal and saw that the kacpid process is taking up between 60-80% of my processor resources. Is there anyway i can get this to trottle down or just turn it off without reprocution?

this is on a ABS Mayhem Eclipse Laptop

specs: 

AMD Turion(tm) 64 Mobile Technology MT-37 - 2000.000 MHz
2GB RAM
100GB HDD
ATI Radeon Mobility x700 

i read the forums and couldnt find anyone else with the same problem.
ill gladly provide any further information needed for troubleshooting.

any help would be greatly apreciated.

thnx

almost forgot:

Ubuntu x86 64bit hardy heron 8.04
kernel 2.6.24-19-generic
gnome 2.22.2

---

### Post by Midgett on 2008-07-05
update on the situation

here are several things i tried:

root@predator-laptop:~# apt-get install acpi acpid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
acpi is already the newest version.
acpid is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

root@predator-laptop:~# modprobe acpi
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.24-19-generic/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): Device or resource busy
root@predator-laptop:~# modprobe acpid
FATAL: Module acpid not found.
root@predator-laptop:~# 

ontop of that i went to synaptics and installed almost all acpi tools i could find but they didnt fix the problem either.

here is the "top" readout

Tasks: 109 total,   4 running, 105 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.0%us, 85.0%sy,  4.3%ni,  0.0%id,  0.0%wa,  1.7%hi,  0.0%si,  0.0%st
Mem:   2062636k total,  1105912k used,   956724k free,    23160k buffers
Swap:  4016208k total,        0k used,  4016208k free,   677640k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM   COMMAND            
   42 root      15  -5     0    0    0 R 85.9  0.0   kacpid             
 9477 predator  20   0  514m 100m  25m S  5.0  5.0   firefox            
10553 predator  39  19 49912  19m  14m R  4.7  0.9   apt-check          
 8554 root      20   0  307m  76m  22m S  1.3  3.8   Xorg               
 4776 root      15  -5     0    0    0 S  0.7  0.0   rt2500pci          
 9255 predator  20   0  213m  22m 6616 S  0.7  1.1   compiz.real        
10176 predator  20   0  275m  25m  11m R  0.7  1.3   gnome-terminal     
    1 root      20   0  4020  884  592 S  0.0  0.0   init               
    2 root      15  -5     0    0    0 S  0.0  0.0   kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   khelper            
   39 root      15  -5     0    0    0 S  0.0  0.0   kblockd/0          
   43 root      15  -5     0    0    0 S  0.0  0.0   kacpi_notify       
  124 root      15  -5     0    0    0 S  0.0  0.0   kseriod            

and no matter what i do it wont let me kill kacpid or kacpi_notify

id really apreciate some advice at this point running out of things to try
any suggestions are welcome

---

