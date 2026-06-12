---
title: "virtual machine"
date: 2009-09-17
forum: x86 64-bit Users
---

### Post by pacco on 2009-09-17
Please forgive my english if im not clear:

I have ubuntu 9.04 64 bit server running,to be exact samba,mail,dns,web server.

I have virtual box installed as well,i want to create a vm say for example an ubuntu vm so that anyone on the internet can use it.

Is there any way pssible and is it safe?
Thanks in advance

---

### Post by sanderj on 2009-09-17
If you're behind a NAT-device (a router, cable/DSL-modem) you have to setup port forwarding on your NAT-device.

And it's probably the easieast way in VirtualBox to select network-type DHCP (and not NAT). Otherwise you would have two NAT-translations after each other.

Logging on can be done using ssh.

---

### Post by pacco on 2009-09-17
Thnk you for the reply

ok i got all my ports forwarded,so now how do i set this up?

---

