---
title: "Kernel 2.6 with Boot root over NFS (root=/dev/nfs) on"
date: 2005-11-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by deen on 2005-11-16
I'm looking the kernel (vmlinux) ubuntu 5.10  Compiled with options boot root over NFS
(example root=/dev/nfs rootfs=10.26.1.1:/some/nfsexports )

the current kernel is not yet compiled with that option

I need it to make ubuntu able to do Diskless booting (dhcpd,tftpd,yaboot,nfs started on server)

my Mac can do "boot enet:0,yaboot" to server

it just vmlinux default kernel don't support boot root over NFS

I dont have gnu-make and some library to build kernel my self and I dont have Harddrive in my Mac, so I asking for help to build this kernel specific setting turned on

Thank you for your help,
I'd really dont know where else to go to get this kernel

---

