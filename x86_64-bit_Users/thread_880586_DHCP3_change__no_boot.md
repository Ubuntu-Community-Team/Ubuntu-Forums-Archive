---
title: "DHCP3 change / no boot"
date: 2008-08-05
forum: x86 64-bit Users
---

### Post by ScottyPDX on 2008-08-05
I've been using Hardy Heron since it became available for the masses with NO Problems, then all of a sudden, the boot process stops, errors out, then gives me a terminal. The error says "looking for host name" in /etc/dhcp3/dhcpd.config line 6. I go to the file (created by Firefox) and all the addresses say 0.0.0.0, and the line 6 says "Hostname <Dynamic>". Anyone know anything about this problem? I try booting with different kernels, but get the same error and no desktop. I have installed so much stuff I really don't want to re-install. Please help.

System:

HP Slimline w/AMD 64 Dual Core, 2 Gigs RAM, NVidia GeForce 6 Series Video card, NVidea N-Force Network card, DSL. I also run dual boot with Vista, which boots fine.

---

### Post by cariboo on 2008-08-05
Have a look here:

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch08_:_Configuring_the_DHCP_Server#The_.2Fetc.2Fdhcpd.conf_File](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch08_:_Configuring_the_DHCP_Server#The_.2Fetc.2Fdhcpd.conf_File)

This should help you troubleshoot your problem. You should also map your computer name to it's ip address in /etc/hosts

Jim

---

