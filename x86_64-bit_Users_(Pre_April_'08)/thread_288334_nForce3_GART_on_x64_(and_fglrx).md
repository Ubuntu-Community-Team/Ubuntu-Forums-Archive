---
title: "nForce3 GART on x64? (and fglrx)?"
date: 2006-10-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by sbfisher on 2006-10-29
Ok, so I'm not sure if this is the best place for this post since it could conceivably go in 3 categories and I'm something of ubuntu newbie.  The short story is that I'm trying ot install fglrx graphics support on Edgy and I think I'm being prevented from getting 3D acceleration by the wrong GART driver.  Motherboard: Asus K8N(nForce 3, 250 chipset); Video card: ATI X1300, x64 version of Edgy.

I followed the instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")  (option 1).  Everything seems to work but fglrxinfo doesn't show acceleration as it should and shows SGI instead of ATI.  This is on a fresh install of Edgy.

```
dmesg | grep fglrx
``` shows:
```
[   68.294759] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   68.299509] [fglrx] Maximum main memory to use for locked dma buffers: 857 MBytes.
[   68.299765] [fglrx] module loaded - fglrx 8.28.8 [Aug 17 2006] on minor 0
[   70.041867] [fglrx] AGP GART is configured for kernel IOMMU, internal GART will not be used
[   70.041876] [fglrx] Internal AGP is not supported in 2.6 kernel.
[   70.042326] [fglrx:firegl_unlock] *ERROR* Process 4166 using kernel context 0
```

So the smattering about GARTs in the errors made me wonder what was going on and I found [this from the ATI site]("http://www2.ati.com/drivers/linux/linux_8.12.10.html") which talks about getting GART set up "X Fails to Load on Systems with Linux Kernel Version 2.6.x."  Though it's not failing to load at the moment it seems to be falling back to something less than fully using the acceleration I'm supposed to be getting (and it did fail to load on non-fresh install before I blew it away.)

I followed some of the ATI instructions ```
sudo lspci | grep AGP
``` to get 
```
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
``` (makes sense).

The instructions (step 3) tell me to look for a module that suits my AGP controller with ```
ls /lib/modules/`uname -r`/kernel/drivers/char/agp
```.  The only things listed are ```
intel-agp.ko  sis-agp.ko  via-agp.ko
```. Since my chipset is nVidia (not any of these types) **am I completely borked with ever getting this to work?** Or if I can get it working, how would I go about it?  Or am I completely wrong in thinking my problems stem from bad nForce3 GART support?

I did see nForce drivers on nVidia's web site at [http://www.nvidia.com/object/linux_nforce_1.0-0275.html]("http://www.nvidia.com/object/linux_nforce_1.0-0275.html") though they seem rather old and nothing particularly Ubuntu or Debian oriented.  But before I went wasting tons of time and destroying my Ubuntu install (again) I thought I'd check to see if this is what I need to do and any indication of how to do it.

---

### Post by John.Michael.Kane on 2006-10-30
You can have look over this [http://ubuntuforums.org/showthread.php?t=185557&highlight=ati](http://ubuntuforums.org/showthread.php?t=185557&highlight=ati)


There has been some users who had issue with that guide you linked to.I'm  not sure why though.

---

### Post by sbfisher on 2006-11-03
Thanks for the info.  After reading some posts on the internet about similar problems I decided to move back to a 32-bit version of edgy.  The driver installed and seemed to be working for a little while on 32-bit version, but then stopped working.

Tried again and now am getting "mesa" driver with fglrxinfo.  Grr.  Most relevant message seems to be [B] [fglrx] Internal AGP is not supported in 2.6 kernel.
[/B]

---

