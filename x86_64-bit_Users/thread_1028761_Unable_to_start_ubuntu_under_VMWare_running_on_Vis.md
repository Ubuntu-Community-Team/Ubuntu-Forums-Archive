---
title: "Unable to start ubuntu under VMWare running on Vista"
date: 2009-01-02
forum: x86 64-bit Users
---

### Post by avrionis on 2009-01-02
Tried both VMware server and player.  VMware install properly along with Ubuntu installing properly.  Once I get ubuntu asking to reboot without the ubuntu install disk, I see the VMware boot messages and then the screen is blank, no ubuntu login.  I trieed resetting and poweroff/on under wvmware but the results are the same.  I tried checking out the vmware log file, no serious errors appear but gets alot of the following messages and then timeouts 

Jan 02 18:22:21.646: vcpu-0| VMSAMPLE32: cs=0x0, eip=0x649
Jan 02 18:22:22.646: vcpu-0| VMSAMPLE32: cs=0x0, eip=0x649
Jan 02 18:22:23.647: vcpu-0| VMSAMPLE32: cs=0x0, eip=0x649
Jan 02 18:22:24.646: vcpu-0| VMSAMPLE32: cs=0x0, eip=0x649


help is much appreciated.

---

### Post by dcstar on 2009-01-02
> **avrionis said:**
> Tried both VMware server and player.  VMware install properly along with Ubuntu installing properly.
.......


At the last stage of the install you can specify the Grub boot device, I have seen problems like that when it is left at default.

I make it a policy to manually set this whenever I install Ubuntu, it just seems to avoid this sort of problem.

---

### Post by avrionis on 2009-01-03
You are right.  Just found this out accidentally. I would disable the GRUB boot loader in the advance setup just before it starts to install.  Once I left it in default but allocated to the proper disk, all went well.  I am now up and running

---

### Post by sherriesyo on 2009-01-03
I want to say,that is WOO! move me we are a good site for age of conan game.If you need [AOC Gold](http://www.mmonice.com/),[Age of Conan Gold](http://www.mmonice.com),[Age of Conan Power Leveling](http://www.mmonice.com/) ,[Age of Conan PowerLeveling](http://www.mmonice.com/),[age of conan](http://www.mmonice.com/) service,come here!

---

