---
title: "Looking for direction: questions on the use of KVM and VT hardware"
date: 2007-06-01
forum: x86 64-bit Users (Pre April '08)
---

### Post by explainer on 2007-06-01
I need some help in configuring KVM as a Virtual Machine Manager. I have Feisty amd64 installed on a dual-core 64 bit AMD processor. As I understand it, the Feisty kernel has VT hooks built into it. All that needs to be done to enable KVM is to install the package. That is what I get from the package documentation. When I run KVM, I get the following:

kvm
open /dev/kvm: No such file or directory
Could not initialize KVM, will disable KVM support

Sure enough /dev/kvm does not exist. How does this file or directory get created?

---

### Post by RAOF on 2007-06-01
You run "sudo modprobe kvm-amd" (for AMD processors, of course).

You could also add "kvm-amd" to the bottom of /etc/modules to have it auto-loaded on boot.

---

### Post by explainer on 2007-06-01
Aha! I shoulda used the ol'  "sudo modprobe kvm-amd" magic incantation.  Thanks very much.  I have used kvm to launch the linux appliance that is available with qemu, so things are looking good.  

So, stated another way, Feisty ships with kvm support, but you must install the kvm package and plug in (modprobe) the correct driver (kvm-amd) in order to get everything set up.  After that, use the kvm command with the qemu command options, right? 

I must study more about loadable kernel modules...

---

### Post by RAOF on 2007-06-03
> **explainer said:**
> ...
So, stated another way, Feisty ships with kvm support, but you must install the kvm package and plug in (modprobe) the correct driver (kvm-amd) in order to get everything set up.  After that, use the kvm command with the qemu command options, right? 
...

Exactly.  Of course, you could make the kernel load that module on boot by adding it to /etc/modules

---

