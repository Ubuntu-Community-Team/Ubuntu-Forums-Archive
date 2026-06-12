---
title: "usb hard drive, usb-storage, amd64-k8-smp"
date: 2006-02-06
forum: x86 64-bit Users (Pre April '08)
---

### Post by coredump25 on 2006-02-06
Cheers,

External USB hard drives are not being detected
with kernel
2.6.12-10-amd64-k8-smp
on Breezy 5.10.

The drives do work with an i386 laptop running Breezy 5.10.

Even after I manually load ehci_hcd, ohci_hcd, and usb_storage modules,
no device is created in /sys/block.

This is a dual core, amd64, with two internal sata drives (/dev/sda and /dev/sdb).

A /sys/block/sdc should be found when the drive is plugged in
while the above modules are loaded.

Using a vanilla kernel, 2.6.15.2, compiled using
the configuration from
2.6.12-10-amd64-k8-smp, the devices are detected
only after rmmod the above drivers and then modprobe them
again.

The made one change to the new kernel's configuration,
that is, I compiled usbcore as a module.

Did anybody have a similar problem with usb hard drives
and figure out a solution?

Thanks.

---

