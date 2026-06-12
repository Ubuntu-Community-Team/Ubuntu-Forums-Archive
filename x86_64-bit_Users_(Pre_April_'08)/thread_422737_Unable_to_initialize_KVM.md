---
title: "Unable to initialize KVM"
date: 2007-04-25
forum: x86 64-bit Users (Pre April '08)
---

### Post by RoboRat on 2007-04-25
I am trying to run KVM using this guide:
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

The kvm and kvm-intel modules install ok but I get an unable to initialize kvm error each time run the virtual machine as per guide:
kvm -no-acpi -m 384 -cdrom /dev/cdrom -boot d windows.img

I'm using a Core 2 Duo E6420 on a Gigabyte DS3P w/ VT enabled in bios.

Can anyone help?

Thanks in advance.

RR

---

### Post by diesel1 on 2007-04-25
> **RoboRat said:**
> I am trying to run KVM using this guide:
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

The kvm and kvm-intel modules install ok but I get an unable to initialize kvm error each time run the virtual machine as per guide:
kvm -no-acpi -m 384 -cdrom /dev/cdrom -boot d windows.img

I'm using a Core 2 Duo E6420 on a Gigabyte DS3P w/ VT enabled in bios.

Can anyone help?

Thanks in advance.

RR


I think you may need to put -hda(or what ever you want your virtual drive to be labelled) in the command before the windows.img.

I also found using this command seemed to do the same...

qemu-system-x86_64 -hda vdisk.raw -cdrom /dev/cdrom -boot d -m 384

You need to substitute your own disk image and options.

Diesel1.

---

### Post by Zed on 2007-04-28
you need to

```

sudo modprobe kvm-intel

``` 

first. (or kvm-amd.) And make sure you have write access to /dev/kvm.

---

