---
title: "help installing vpn client"
date: 2008-01-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by ghettosamson on 2008-01-10
Just a question to help get me started. I am running gutsy gibbins x64 and I need a vpn client for school. Is there a cisco vpn client that suppors 64 bit architecture? I ask because I am trying to install the most recent cisco vpn client which is vpnclient-linux-x86_64-4.8.01.0640-k9.tar.gz
and i cant get it to work. This is the error i get.
=================================
Cisco Systems VPN Client Version 4.8.01 (0640) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms.


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]yes

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.22-14-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.22-14-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.22-14-generic/build" will be used to build the module.

Is the above correct [y]y

Making module
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/spanish/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
CC [M] /home/spanish/Desktop/vpnclient/interceptor.o
In file included from /home/spanish/Desktop/vpnclient/Cniapi.h:15,
from /home/spanish/Desktop/vpnclient/interceptor.c:34:
/home/spanish/Desktop/vpnclient/GenDefs.h:110:2: warning: #warning 64 bit
/home/spanish/Desktop/vpnclient/interceptor.c: In function ‘recv_ip_packet_handler’:
/home/spanish/Desktop/vpnclient/interceptor.c:639: warning: assignment makes integer from pointer without a cast
/home/spanish/Desktop/vpnclient/interceptor.c:660: warning: passing argument 2 of ‘CniNewFragment’ makes pointer from integer without a cast
/home/spanish/Desktop/vpnclient/interceptor.c: In function ‘do_cni_send’:
/home/spanish/Desktop/vpnclient/interceptor.c:778: error: invalid operands to binary -
make[2]: *** [/home/spanish/Desktop/vpnclient/interceptor.o] Error 1
make[1]: *** [_module_/home/spanish/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
=====================================
Hope some one can help. thank you

---

### Post by mr_waters on 2008-01-17
You could try **vpnc** its a cisco compatible vpn client. Theres also a gui for the network manager called **network-manager-vpnc **. I got it from the package manager.

PS: I found the homepage.
[http://www.unix-ag.uni-kl.de/~massar/vpnc/](http://www.unix-ag.uni-kl.de/~massar/vpnc/)
 
Cheers

---

### Post by jdos2 on 2008-01-30
I'm havin' the same trouble.

I have to use Cisco's client for the RSA key device, so other software isn't an option.
I'll post back with success.

---

### Post by glhewett on 2008-02-04
Hi, did you ever find the solution to this problem?  I am having the same issue.

---

