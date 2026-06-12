---
title: "Intel D975BX2, No Network."
date: 2008-10-09
forum: x86 64-bit Users
---

### Post by mkaylor on 2008-10-09
I have a Intel D975BX2 (BadAxe2) Motherboard and when I loaded 8.10Beta 64-Bit, the network will not work.  It works fine under 32-Bit.  It also works under OpenSuse 11 64-Bit.

I now have 8Gigs of ram and need the 64-Bit to access it all.

The network controller is a Gigabit (10/100/1000 Mbits/sec) LAN subsystem using the Intel® 82573E/82573L Gigabit Ethernet Controller.

I may have posted this in the wrong forum.  Any help would be greatly appreciated.

Thanks,
Mike

---

### Post by Yellow Pasque on 2008-10-09
If you could provide some output, we can see where the problem lies (hardware, driver, interface, etc.): Please post output of:
```
sudo lshw -C network
cat /etc/network/interfaces
ifconfig
```

---

### Post by mkaylor on 2008-10-10
kaylor@dolphin:~$ sudo lshw -C network

DMI
SMP
PA-RISC
device-tree
SPD
memory
/proc/cpuinfo
CPUID
PCI (sysfs)
ISA PnP
PCMCIA
PCMCIA
kernel device tree (sysfs)
USB
IDE
SCSI
Network interfaces
Framebuffer devices
Display
CPUFreq
ABI
  *-network UNCLAIMED
       description: Ethernet controller
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2e:36:39:83:64:a9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


mkaylor@dolphin:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

mkaylor@dolphin:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6984 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6984 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:355432 (355.4 KB)  TX bytes:355432 (355.4 KB)

Not being sure of what I was doing.  I tried bringing pan0 up with an #ifconfig pan0 up.  The interface came up but still does not work.  I didn't think it would.

Thanks for any help,
Mike

---

### Post by Yellow Pasque on 2008-10-10
You have an Intel ethernet chipset that is affected by a bug.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555)

The upshot of this is to make sure you update to the 2.6.27-6 kernel and then remove the e1000e driver from /etc/modprobe.d/blacklist (there may also be an /etc/modprobe.d/blacklist-e1000e file that you have to delete).

---

