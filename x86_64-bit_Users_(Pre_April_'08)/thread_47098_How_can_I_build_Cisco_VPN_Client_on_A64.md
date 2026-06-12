---
title: "How can I build Cisco VPN Client on A64?"
date: 2005-07-07
forum: x86 64-bit Users (Pre April '08)
---

### Post by pingp on 2005-07-07
I tired to build Cisco VPN Client on 2.6.10 X86_64 Kernel, but always got same error.
the key word seemed as  **/opt/vpnclient/GenDefs.h:111:2: warning: #warning 64 bit**
.Thanx alot, need help


Making module
make -C /lib/modules/2.6.10-5-amd64-generic/build SUBDIRS=/opt/vpnclient modulesmake[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-amd64-generic'
  CC [M]  /opt/vpnclient/linuxcniapi.o
In file included from /opt/vpnclient/Cniapi.h:15,
                 from /opt/vpnclient/linuxcniapi.c:30:
/opt/vpnclient/GenDefs.h:101:2: warning: #warning 64 bit
In file included from /opt/vpnclient/Cniapi.h:15,
                 from /opt/vpnclient/linuxcniapi.c:30:
/opt/vpnclient/GenDefs.h:102: error: syntax error before "intptr_t"
/opt/vpnclient/GenDefs.h:102: warning: type defaults to `int' in declaration of `intptr_t'
/opt/vpnclient/GenDefs.h:102: warning: data definition has no type or storage class
/opt/vpnclient/GenDefs.h:111:2: warning: #warning 64 bit
/opt/vpnclient/linuxcniapi.c: In function `os_alloc':
/opt/vpnclient/linuxcniapi.c:47: warning: int format, different type arg (arg 2)make[2]: *** [/opt/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/opt/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-amd64-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

---

### Post by joekr on 2005-07-07
Have you tried searching for a Cisco VPN Client in Synaptic?

---

### Post by NickB on 2005-07-08
I've used vpnc with great success connecting to Cisco equipment.

Nick

---

### Post by Mad Leguan on 2005-07-29
i have the same problem right now,
if you have got it to work, what have you done
i followed the normal instruction but it don't work

---

