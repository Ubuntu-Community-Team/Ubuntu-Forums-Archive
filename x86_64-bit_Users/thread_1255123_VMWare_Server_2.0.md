---
title: "VMWare Server 2.0"
date: 2009-09-01
forum: x86 64-bit Users
---

### Post by keithdrayton on 2009-09-01
Hello

Im very much a Ubuntu novice so please stick with me through any daft questions.

Im looking to install Ubuntu 9.04 64bit onto a workstation and then use VMWare server 2 on top.
I found this page about installing VMWare Server
[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)
I followed that fine on a 32bit test system,

My question is do i still need apply the patch to a 64bit version of vmware server, will the 'How to' work for me on 64bit?

Thanks
Keith

---

### Post by yotis on 2009-09-01
Hi there!

I have a 64bit Ubuntu 9.04 system, and I installed Vmware server 2 as it came from the vmware.com servers, without any patch and it's working fine.

A small note has to be mentioned here. Even if it's working great, there is a small issue, which require a little bit of extra work. After kernel update, when running "vmware-config.pl", it gives me an error due to the fact that it cannot build vsock module (the rest of module, setting, etc are fine). I solve this vsock module following this tutorial: [http://kramfs.com/vmware-server-2-unable-to-build-the-vsock-module/](http://kramfs.com/vmware-server-2-unable-to-build-the-vsock-module/)

Maybe the patch is solving this issue, I don't know really...

---

### Post by keithdrayton on 2009-09-01
Hi Yotis

I dont recall that problem on the 32bit test system so think i will patch it and see what happens,

The ubuntu install went fine,
Eventually got everything working trough our proxy service.
Followed a 'How To' for windows AD authentication - That failed, but will come back to that later, i dont think it really needs it.
Once the download completes will look at the VMserver install and get that running.

---

