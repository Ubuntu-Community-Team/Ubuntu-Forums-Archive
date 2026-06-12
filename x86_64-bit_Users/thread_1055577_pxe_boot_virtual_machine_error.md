---
title: "pxe boot virtual machine error"
date: 2009-01-30
forum: x86 64-bit Users
---

### Post by mk6032 on 2009-01-30
I open VM manager, create new using QEMU, PXE boot installation, 4gb allocated, 512 MB ram. It creates the image, then when it goes to complete it stops and says:

Unable to complete install '<class 'libvirt.libvirtError'> virDomainCreateLinux() failed internal error QEMU quit during console startup
No valid PXE rom found for network device

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/create.py", line 652, in do_install
    dom = guest.start_install(False, meter = meter)
  File "/usr/lib/python2.5/site-packages/virtinst/Guest.py", line 902, in start_install
    return self._do_install(consolecb, meter)
  File "/usr/lib/python2.5/site-packages/virtinst/Guest.py", line 923, in _do_install
    self.domain = self.conn.createLinux(install_xml, 0)
  File "/usr/lib/python2.5/site-packages/libvirt.py", line 841, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: virDomainCreateLinux() failed internal error QEMU quit during console startup
No valid PXE rom found for network device

screenshot...
[IMG]http://i42.tinypic.com/2nkqsua.jpg[/IMG]

---

