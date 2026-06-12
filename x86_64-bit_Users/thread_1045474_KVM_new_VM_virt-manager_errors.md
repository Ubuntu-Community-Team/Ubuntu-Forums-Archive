---
title: "KVM new VM virt-manager errors"
date: 2009-01-20
forum: x86 64-bit Users
---

### Post by cderigo on 2009-01-20
I am brand new to Linux, much less Ubuntu. I have been wanting to make the jump from windows for a while and finally decided to do it. Unfortunately, I have a few applications that I need to run on Windows Server 2003. I built a new machine with the Intel core i7 and a bunch of ram to run virtualization. I am running Ubuntu Server 64 8.10. I initially tried to use Xen for Virtualization, but found that it is not supported in 8.10, so 
I went with KVM which appeared to be OOB. I seem to have it running, I've created another Ubuntu vm, but everything fails when creating my windows vm. Here is the error I get when attempting to install:

Unable to complete install '<class 'libvirt.libvirtError'> virDomainCreateLinux() failed internal error invalid domain type attribute
Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/create.py", line 652, in do_install
    dom = guest.start_install(False, meter = meter)
  File "/usr/lib/python2.5/site-packages/virtinst/Guest.py", line 902, in start_install
    return self._do_install(consolecb, meter)
  File "/usr/lib/python2.5/site-packages/virtinst/Guest.py", line 923, in _do_install
    self.domain = self.conn.createLinux(install_xml, 0)
  File "/usr/lib/python2.5/site-packages/libvirt.py", line 841, in createLinux
    if ret is None:raise libvirtError('virDomainCreateLinux() failed', conn=self)
libvirtError: virDomainCreateLinux() failed internal error invalid domain type attribute
'

I am in need of real help here. I don't even know where to begin on this.

---

### Post by starfry on 2009-01-21
I want to do this too. I've heard scare stories about core i7 and Linux in general. Risking going off topic would you be willing to share your hardware specs it sounds like you are doing exactly what I want to!

Re the virtualisation, have you tried VirtualBox ? I use it now but on a machine busting at the seams. I am running it on 8.10 albeit 32 bit. I want to upgrade to core i7 and run 65 bit with 12Gb ram so I can run several VMs.

---

### Post by cderigo on 2009-01-21
core i7 920
intel DX58SO MB
6 gig OCZ 12800 DDR3
gforce 8500 GT graphocs
(4) 500gig 32mg cache 7200 rpm sata drives

That's about it...

---

