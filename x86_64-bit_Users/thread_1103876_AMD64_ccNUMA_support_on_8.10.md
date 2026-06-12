---
title: "AMD64 ccNUMA support on 8.10?"
date: 2009-03-23
forum: x86 64-bit Users
---

### Post by eugenwinter on 2009-03-23
Hi there. I am using a system with 2 dual core Opterons. Each of the CUPs has its own memory controller (as mentioned by the AMD manual). According to the AMD software optimization guide for AMD64 the "system" how the CPUs are connected with the memory is called "ccNUMA". Furthermore, the AMD manual states that SUSEs AMD64 kernel supports the ccNUMA architecture of AMD. Does anyone know whether the 8.10 AMD64 default kernel supports ccNUMA or not?

thanks 
   Eugen Wintersberger

---

### Post by dcstar on 2009-03-24
> **eugenwinter said:**
> Hi there. I am using a system with 2 dual core Opterons. Each of the CUPs has its own memory controller (as mentioned by the AMD manual). According to the AMD software optimization guide for AMD64 the "system" how the CPUs are connected with the memory is called "ccNUMA". Furthermore, the AMD manual states that SUSEs AMD64 kernel supports the ccNUMA architecture of AMD. Does anyone know whether the 8.10 AMD64 default kernel supports ccNUMA or not?

thanks 
   Eugen Wintersberger

Install the kernel source package and look in the .config file.

---

### Post by bismark on 2009-03-24
I think so, here is the NUMA lines from the default x86_64 config file.
```

$ uname -a
Linux battleship 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux

$ grep -i numa /boot/config-2.6.27-11-generic
CONFIG_ACPI_NUMA=y
CONFIG_K8_NUMA=y
CONFIG_NUMA=y
# CONFIG_NUMA_EMU is not set
CONFIG_X86_64_ACPI_NUMA=y

```

---

### Post by Em-Buntu on 2009-03-24
Yes, Ubuntu AMD64 fully supports cc (Cache Coherent) NUMA.
The OS will see memory across the two CPUs.
Example:
CPU1 has 1GB RAM + CPU2 has 1GB, the system will report 2GB of system memory.

In fact, even Ubuntu 6.04 fully supports NUMA.

---

