---
title: "[feisty] Xen vnc console not working"
date: 2007-04-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by melix007 on 2007-04-18
Hi,

I'm having troubles setting up a windows guest in Feisty. I have installed the Feisty server amd64 edition on an Opteron 2210 system, and installed the xen-hypervisor, tools and so on in order to have a complete setup. The problem is that as it is a server, there's no X server, and I'd like to setup a vnc console in order for remote hosts to complete the installation.

Here's my VM configuration :

```
kernel = "/usr/lib/xen-ioemu-3.0/boot/hvmloader"
builder = 'hvm'
memory = 512
name = "winxp"
vcpus = 1
vif = [ 'type=ioemu, bridge=xenbr0' ]
disk = [ 'file:/opt/xen/images/WinXP.img,ioemu:hda,w' ]
device_model = '/usr/lib/xen-ioemu-3.0/bin/qemu-dm'
cdrom='/dev/cdrom'
ne2000=0
boot='d'
vnc=1
vncviewer=0

```

The problem is that the vnc server never spawns. Worse, the VM shutdowns instantly, with the following qemu log :

```
domid: 73
qemu: the number of cpus is 1
shared page at pfn:1ffff, mfn: 41ded
buffered io page at pfn:1fffd, mfn: 41def
False I/O request ... in-service already: 0, pvalid: 0, port: 0, data: 0, count: 0, size: 0

```

I've also tried several configurations (vnclisten, vncdisplay, ...) without success. If I try "vnc=0, vncviewer=1", the VM does not shutdown, but I've got an error in the qemu log telling there's no framebuffer (I think it's logic since there's no X server).

Any idea ? Is VNC broken in xen-ioemu on amd64 ?

---

### Post by melix007 on 2007-04-18
Got it thanks to xm dmesg : it was cdrom...

For info, here's the correct configuration :

```
kernel = "/usr/lib/xen-ioemu-3.0/boot/hvmloader"
builder = "hvm"
memory = "512"
name = "winxp"
vcpus = "1"
vif = [ 'type=ioemu, bridge=xenbr0' ]
disk = [ 'file:/var/xen/images/winxp.img,ioemu:hda,w', 'phy:/dev/cdrom,hdb:cdrom,r']
device_model = "/usr/lib/xen-ioemu-3.0/bin/qemu-dm"
ne2000 = "0"
boot = "d"
sdl=0
vncviewer=0
vnc=1
stdvga=0
serial='pty' 

```

---

