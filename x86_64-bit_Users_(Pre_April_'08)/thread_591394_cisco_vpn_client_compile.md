---
title: "cisco vpn client compile"
date: 2007-10-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by sperry on 2007-10-25
after 7.04_64 upgrade to 7,10_64 cisco vpn client will not compile
get this error:
] ./vpn_install
Cisco Systems VPN Client Version 4.8.01 (0640) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.22-14-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.22-14-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.22-14-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/data/download/vpn/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /data/download/vpn/vpnclient/interceptor.o
In file included from /data/download/vpn/vpnclient/Cniapi.h:15,
                 from /data/download/vpn/vpnclient/interceptor.c:34:
/data/download/vpn/vpnclient/GenDefs.h:110:2: warning: #warning 64 bit
/data/download/vpn/vpnclient/interceptor.c: In function ‘recv_ip_packet_handler’:
/data/download/vpn/vpnclient/interceptor.c:639: warning: assignment makes integer from pointer without a cast
/data/download/vpn/vpnclient/interceptor.c:660: warning: passing argument 2 of ‘CniNewFragment’ makes pointer from integer without a cast
/data/download/vpn/vpnclient/interceptor.c: In function ‘do_cni_send’:
/data/download/vpn/vpnclient/interceptor.c:778: error: invalid operands to binary -
make[2]: *** [/data/download/vpn/vpnclient/interceptor.o] Error 1
make[1]: *** [_module_/data/download/vpn/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

think it might be a lib problem, but i'm not sure where to start

has anyone had similar problems
anyone tried on a fresh install

---

### Post by peteguhl on 2007-10-26
[http://ubuntuforums.org/showthread.php?p=3637667#post3637667](http://ubuntuforums.org/showthread.php?p=3637667#post3637667)

---

