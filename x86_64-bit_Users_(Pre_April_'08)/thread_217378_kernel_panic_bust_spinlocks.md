---
title: "kernel panic bust_spinlocks"
date: 2006-07-17
forum: x86 64-bit Users (Pre April '08)
---

### Post by topgun_ca on 2006-07-17
I am getting kernel panics when I am running "stress" on the system to do a initial stress test before I start putting real work on it.
$ apt-get install stress
$stress --cpu 12 --io 10 --vm 10 --vm-bytes 128M --timeout 100000s --verbose

I have attached a copy of memtest and the console output that I got through KVM when the server died.

Here are some of the entries in the log files:
dmesg
[    0.000000] ACPI: Unable to locate RSDP
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: TYAN     <6>Product ID: S2881        <6>APIC at: 0xFEE00000
[    0.000000] Processor #0 15:5 APIC version 16
[    0.000000] I/O APIC #1 Version 17 at 0xFEC00000.
[    0.000000] I/O APIC #2 Version 17 at 0xFEBFF000.
[    0.000000] I/O APIC #3 Version 17 at 0xFEBFE000.
[   33.869489] Using IO-APIC 1
[   33.869495] Using IO-APIC 2
[   33.869497] Using IO-APIC 3
[   34.120904] ACPI: Subsystem revision 20051216
[   34.120906] ACPI: Interpreter disabled.
[   34.123482] PCI: MSI quirk detected. pci_msi_quirk set.
[   34.123486] PCI: MSI quirk detected. pci_msi_quirk set.



/var/log/messages
Jul 16 17:02:36 srv1 kernel: [ 2435.535458] Machine check events logged
Jul 16 17:07:36 srv1 kernel: [ 2735.003362] Machine check events logged
Jul 16 17:12:36 srv1 kernel: [ 3034.461297] Machine check events logged
Jul 16 17:17:36 srv1 kernel: [ 3333.929201] Machine check events logged
Jul 16 17:22:36 srv1 kernel: [ 3633.397107] Machine check events logged
Jul 16 17:27:36 srv1 kernel: [ 3932.875013] Machine check events logged
Jul 16 17:32:36 srv1 kernel: [ 4232.352889] Machine check events logged
Jul 16 17:37:36 srv1 kernel: [ 4531.820809] Machine check events logged
Jul 16 17:42:36 srv1 kernel: [ 4831.288708] Machine check events logged
Jul 16 17:47:36 srv1 kernel: [ 5130.756612] Machine check events logged
Jul 16 17:52:36 srv1 kernel: [ 5430.224522] Machine check events logged
Jul 16 17:57:36 srv1 kernel: [ 5729.692441] Machine check events logged
Jul 16 19:10:05 srv1 kernel: [   34.995486] PCI: MSI quirk detected. pci_msi_quirk set.
Jul 16 19:10:05 srv1 kernel: [   34.995489] PCI: MSI quirk detected. pci_msi_quirk set.



How do I troubleshoot it ?

---

### Post by amcquown on 2006-07-17
Make sure your RAM is good - I got something similar just trying to boot Ubuntu from a LiveCD - turns out I had a faulty RAM stick. Removed, re-tested, installed Ubuntu - no problems :)

---

