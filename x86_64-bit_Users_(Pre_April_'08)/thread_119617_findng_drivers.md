---
title: "findng drivers"
date: 2006-01-19
forum: x86 64-bit Users (Pre April '08)
---

### Post by who_cares on 2006-01-19
I have a Gigabyte GA-K8NS motherboard with a onboard NIC.
The disk that came with that motherboard had 2 Linux drivers on it but I don't know how to use them or if they are ever compatible with my Kernel (I just started with Linux yesterday)
Does anyone know where I could get a compatible driver?
The chipset is a nForce 3

---

### Post by brainkilla on 2006-01-19
When you installed Ubuntu (the same goes for any other distro) you had already had everything you needed with it. It's not like Windows when you have to spend another 2-3 postinstall hours chasing drivers and getting your 'supported' hardware working. Do you have any specific problem - does USB, sound, NIC, SATA (Linux driver you've got is meant for SATA perhaps?) work properly? Or you just thought you needed 3rd party drivers by simple analogy :) ?

your mobo and linux:

[http://www.linuxquestions.org/hcl/showproduct.php/product/2275/sort/2/cat/all/page/1](http://www.linuxquestions.org/hcl/showproduct.php/product/2275/sort/2/cat/all/page/1)

---

### Post by who_cares on 2006-01-19
Well, my internet doesn't work, I enabled the ethernet connection in the networking "window" and I set it to DHCP.
I rebooted and thought I would at least be able to get to the router config page.
I opened the device manager and it said unknown in a lot of fields for my NIC, so I assumed I needed a driver for it.

---

### Post by brainkilla on 2006-01-19
What does 'lspci' command say (type in terminal without quotes)? The HAL Device manager is bullshit and not like its Windows counterpart which displays useful information actually. And one thing - after adjusting settings there's no need to reboot your machine, start thinking Linux way ;) . When you get lspci output, you can google for it or just ask here what module you need in order to get it working... Also, please post the 'lsmod' output here...

---

### Post by who_cares on 2006-01-19
um..yeah... how do I get to terminal? (I got there once somehow, I don't know for sure)
then I can probably run it

---

### Post by brainkilla on 2006-01-19
Applications-Accessories-Terminal, or hit Alt+F2 and type gnome-terminal

---

### Post by who_cares on 2006-01-19
okay:
> 0000:00:00.0 Host bridge: nVidia Corporation: Unknown device 00e1 (rev a1)
0000:00:01.0 ISA bridge: nVidia Corporation: Unknown device 00e0 (rev a2)
0000:00:01.1 SMBus: nVidia Corporation: Unknown device 00e4 (rev a1)
0000:00:02.0 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.1 USB Controller: nVidia Corporation: Unknown device 00e7 (rev a1)
0000:00:02.2 USB Controller: nVidia Corporation: Unknown device 00e8 (rev a2)
0000:00:05.0 Bridge: nVidia Corporation: Unknown device 00df (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation: Unknown device 00ea (rev a1)
0000:00:08.0 IDE interface: nVidia Corporation: Unknown device 00e5 (rev a2)
0000:00:0a.0 IDE interface: nVidia Corporation: Unknown device 00e3 (rev a2)
0000:00:0b.0 PCI bridge: nVidia Corporation: Unknown device 00e2 (rev a2)
0000:00:0e.0 PCI bridge: nVidia Corporation: Unknown device 00ed (rev a2)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: nVidia Corperation: Unknown device 0221 (rev a1)

---

### Post by brainkilla on 2006-01-19
Pretty useless, since it lack any info on Ethernet... Ok, if this is integrated NIC, it should be 'Marvell Technology Group Ltd. Yukon Gigabit Ethernet' on that particular mobo. Try the following command in terminal 

sudo modprobe sk98lin

this will load appropriate module('driver'); then type

tail -f /var/log/messages

to see what did system say. Anway, try to make a connection as you did previously and if everything works add the following line in /etc/modules

sk98lin (sudo gedit /etc/modules in terminal). 
This will automagically load the module on boot. Also to check your conection you can use the following command

ifconfig

It gives the following output on my machine:

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1508 (1.4 KiB)  TX bytes:1508 (1.4 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:217.26.66.*  P-t-P:217.26.65.*  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:21331 errors:1 dropped:0 overruns:0 frame:0
          TX packets:17641 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:20672535 (19.7 MiB)  TX bytes:1925953 (1.8 MiB)

The first is loopback interface (always present) and the second my little dial-up modem. You should get eth0 instead of ppp0...

---

### Post by who_cares on 2006-01-19
well the sudo/tail commands loaded scsi and failed because I have IDE drives.
and ifconfig lists a ethernet connection and then the loopback

---

### Post by brainkilla on 2006-01-19
Hmmm, I don't quite get it. Tail serves the purpose of reading the system logs, and sudo gives you root (admin) privileges - the actual command is modprobe (='load module/driver') and it loaded a NIC driver, not scsi/ide disks one. Try

ifconfig eth0 up 

and launch firefox, that should be it (if we've got the correct module that is).

---

### Post by who_cares on 2006-01-20
It returned
> ERROR getting interface flags: No suck device

---

### Post by who_cares on 2006-01-20
I guess that error isn't all that bad, I'm using my Linux computer to post this :D

---

