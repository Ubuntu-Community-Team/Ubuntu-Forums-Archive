---
title: "KVM virt-manager failing to create new virtual system"
date: 2008-04-28
forum: x86 64-bit Users
---

### Post by jjrev on 2008-04-28
Here are my failure details:

$ sudo apt-get install kvm libvirt-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  debootstrap etherboot kvm-source
Recommended packages:
  vde2
The following NEW packages will be installed:
  kvm libvirt-bin
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/858kB of archives.
After this operation, 2961kB of additional disk space will be used.
Selecting previously deselected package kvm.
(Reading database ... 97251 files and directories currently installed.)
Unpacking kvm (from .../kvm_1%3a62+dfsg-0ubuntu7_amd64.deb) ...
kvm: Using the existing group "kvm" (gid 125) for /dev/kvm
Selecting previously deselected package libvirt-bin.
Unpacking libvirt-bin (from .../libvirt-bin_0.4.0-2ubuntu8_amd64.deb) ...
Setting up kvm (1:62+dfsg-0ubuntu7) ...
FATAL: Error inserting kvm_intel (/lib/modules/2.6.24-16-generic/kernel/arch/x86/kvm/kvm-intel.ko): Operation not supported
 * Module kvm_intel failed to load
invoke-rc.d: initscript kvm, action "start" failed.

Setting up libvirt-bin (0.4.0-2ubuntu8) ...
 * Starting libvirt management daemon libvirtd                                                                                                                                                [ OK ] 

...

then, when trying to setup the Virtual system:

Unable to complete install '<class 'libvirt.libvirtError'> virDomainCreateLinux() failed QEMU quit during console startup

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/create.py", line 617, in do_install
    dom = guest.start_install(False, meter = meter)
  File "/usr/lib/python2.5/site-packages/virtinst/Guest.py", line 820, in start_install
    return self._do_install(consolecb, meter)
  File "/usr/lib/python2.5/site-packages/virtinst/Guest.py", line 841, in _do_install
    self.domain = self.conn.createLinux(install_xml, 0)
  File "/usr/lib/python2.5/site-packages/libvirt.py", line 585, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: virDomainCreateLinux() failed QEMU quit during console startup

'

I'm running Hardy on 64bit Xeons.  Any ideas?

---

### Post by vishalrao on 2008-04-28
do you have VT enabled in the BIOS? after enabling you need to power down completely then power up again, for it to take effect.

also, you could try adding yourself to the kvm and libvirtd groups in "users and groups" under system menu...

---

### Post by jjrev on 2008-04-28
My BIOS does not support VT, but the 32bit version of Hardy was able to load the module.  I am content to run pure software virtualization until my MOBO manufacturer releases a VT enabled BIOS.

I have already added myself to the proper groups.  

I also checked dmesg for anything kvm related...
```

$ dmesg | grep -i kvm
[   58.840072] kvm: disabled by bios
[  141.527760] kvm: disabled by bios
[  175.015328] kvm: disabled by bios
```

I will re-iterate that the 32bit version of Hardy was able to load the kvm module..

---

