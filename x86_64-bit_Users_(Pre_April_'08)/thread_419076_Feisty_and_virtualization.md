---
title: "Feisty and virtualization"
date: 2007-04-22
forum: x86 64-bit Users (Pre April '08)
---

### Post by brickeen on 2007-04-22
Hello All,

Can anyone confirm that the paravirt-ops and KVM elements are available/present in both the desktop and server versions of Feisty?
Contemplating a re-install and I only use virtualization for testing or to run the odd bit of windows software.
Hardware is an AMDx2 in an ABIT KN9-Ultra.

Best regards,
..

---

### Post by RAOF on 2007-04-23
Yes, they are.

Just an "apt-get install kvm && sudo adduser <yourusername> kvm" away.

Oh, and you need to modprobe the appropriate kernel kvm driver (either kvm-intel or kvm-amd)

---

### Post by brickeen on 2007-04-23
Brilliant.  Thanks for that.
I was hoping to install the Desktop product and get to play with beryl.  But that raisies another quesstion...
Can a KVM guest take advantage of 3D graphics capabilities of the host?

---

