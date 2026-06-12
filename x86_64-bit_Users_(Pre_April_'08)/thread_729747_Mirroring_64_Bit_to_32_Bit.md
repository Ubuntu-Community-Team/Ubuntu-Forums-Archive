---
title: "Mirroring 64 Bit to 32 Bit"
date: 2008-03-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by cikic on 2008-03-20
Hello

I have a 64Bit machine running ubuntu as host and several vmwares running (also ubuntu 64Bit ones). Not we have an "new" old 32Bit server (the machine is no longer in use). Is it possible to use this machine as a mirror? Means, is it possible to mirror a 64Bit ubuntu (guest in a vmware) to a 32Bit vmware? Or is it possible to downgrade a productive running 64Bit ubutnu to 32Bit without the risk of loosing data?

Thanks
Christian

---

### Post by Kilz on 2008-03-20
> **cikic said:**
> Hello

I have a 64Bit machine running ubuntu as host and several vmwares running (also ubuntu 64Bit ones). Not we have an "new" old 32Bit server (the machine is no longer in use). Is it possible to use this machine as a mirror? Means, is it possible to mirror a 64Bit ubuntu (guest in a vmware) to a 32Bit vmware? Or is it possible to downgrade a productive running 64Bit ubutnu to 32Bit without the risk of loosing data?

Thanks
Christian

Since vmware is 32bit it should not be a problem to run any 32bit virtual machines you have running on the 64bit systems. You could not run 64bit virtual machines on a 32bit system only 32bit ones. An example
If I has 32bit Windows XP virtual machine on the 64bit system in Vmware I could transfer the Windows XP to the 32bit hardware.
If I had a 64bit Ubuntu  virtual machine I could not use it on 32bit hardware

---

### Post by cikic on 2008-03-20
Thanks for your Reply. In fact my VM is 64bit ( [http://www.vmware.com/company/news/releases/64bit.html](http://www.vmware.com/company/news/releases/64bit.html) ). 

Hmmm ....  I think there is nothing like 
apt-get remove ubuntu64
apt-get install ubuntu32

 ... seems there will be 32Bit machine for sale :-)

Thank you
Christian

---

