---
title: "Trying to hide a pci device..."
date: 2008-03-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by durb on 2008-03-03
Im trying to hide one of my pci devices at boot but I cant seem to get it to work.  I have tried adding the appropriate pci id with pciback.hide in the grub entry but all I get is a message saying unknown command.  Does anyone know how to do this?

---

### Post by dcstar on 2008-03-05
> **durb said:**
> Im trying to hide one of my pci devices at boot but I cant seem to get it to work.  I have tried adding the appropriate pci id with pciback.hide in the grub entry but all I get is a message saying unknown command.  Does anyone know how to do this?

Have a look at this:

[http://www.nabble.com/debian-etch,-how-to-hide-a-pci-card,-pv---hvm-xen-3.2.0-td15106023.html](http://www.nabble.com/debian-etch,-how-to-hide-a-pci-card,-pv---hvm-xen-3.2.0-td15106023.html)

---

### Post by durb on 2008-03-06
> **dcstar said:**
> Have a look at this:

[http://www.nabble.com/debian-etch,-how-to-hide-a-pci-card,-pv---hvm-xen-3.2.0-td15106023.html](http://www.nabble.com/debian-etch,-how-to-hide-a-pci-card,-pv---hvm-xen-3.2.0-td15106023.html)
Thanks for the last link, it got me going in the right direction.  I installed the ubuntu-xen-desktop package and here is the relevant grub entry:

title		Xen 3.1 / Ubuntu 7.10, kernel 2.6.22-14-xen
root		(hd0,0)
kernel		/boot/xen-3.1.gz
module		/boot/vmlinuz-2.6.22-14-xen root=UUID=a1472b3e-dbc8-4969-92a8-08129351fa02 ro console=tty0 pciback.permissive pciback.hide=(03:00.0)(02:00.0)
module		/boot/initrd.img-2.6.22-14-xen
quiet

but it doesnt seem to work( I can still seem the devices with lspci).  I heard its related to a kernel module so I checked:

sudo modprobe pciback

gives me : FATAL: Module pciback not found.

Do you have any ideas?

---

### Post by hurenkam on 2008-03-09
Hmm, the pciback.hide option you use seems to be ok, although I'm using a leading 0000:, perhaps you should give that a try?

I was also wandering at first why my pciback.hide option in grub didn't work, until I discovered that pciback is built as a module (I built it from the xen sources), and so the options had to be added to /etc/modprobe.d/options:
options pciback hide=(0000:00:04.0)(0000:00:0c.0)(0000:00:0d.0)(0000:02:08.0)(0000:02:09.0)
Then the pciback module needs to be added to /etc/modules, now things are working fine for me.

Starting with xen 3.0.x, the lspci does still show the 'hidden' pci cards, so don't be surprised that the devices still show in lspci output.
You should be able to see in your dmesg output that the hidden devices are claimed by pciback:
pciback 0000:00:04.0: seizing device
pciback 0000:00:0c.0: seizing device
pciback 0000:00:0d.0: seizing device
pciback 0000:02:08.0: seizing device
pciback 0000:02:09.0: seizing device

Mark

---

