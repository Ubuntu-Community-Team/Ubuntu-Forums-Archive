---
title: "Installing Ubuntu with a 1GB USB ms"
date: 2005-04-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by diniz on 2005-04-18
Hi,

here is my problem. I have a machine with no floppy and no CD. It has just USB and network. I'd like to install Ubuntu using my 1GB USB memory stick. So I followed these steps (supposing pendrive is at /dev/sdc):

mkdosfs -I /dev/sdc
mount /dev/sdc /mnt
cp vmlinuz initrd.gz ubuntu.iso /mnt
umount /mnt
syslinux /dev/sdc
mount /dev/sdc /mnt
<edit /mnt/syslinux.cfg>
umount /mnt

ubuntu.iso is the iso image for hoary install (about 600MB). So I booted the machine and it couldn't boot from the USB memory stick. What am I doing wrong?

Thanks,
Bruno.

PS: I have successfully installed Debian 32bits using the memory stick and netinst iso image.

---

### Post by yanik on 2005-04-19
Humm, when you mount your pendrive, do you see the actual ubuntu install files or just ubuntu.iso?  I'm not familiar with pendrives, but I think you should have all the files from the iso and not the iso file itself.

---

### Post by pietro_spina on 2005-04-19
Are you sure you set your system bios to boot from usb before your Hardrive?

---

### Post by tikal26 on 2005-04-23
In my bios I have a choice that says hardrive or remobable crad so when I press 
esc I get an option and I choose my hard drive and then I get a choice between my maxtor or my USB drive.

---

### Post by skimaster18 on 2006-10-23
> **yanik said:**
> Humm, when you mount your pendrive, do you see the actual ubuntu install files or just ubuntu.iso?  I'm not familiar with pendrives, but I think you should have all the files from the iso and not the iso file itself.

you are exactly correct - its just one big iso file and computer doesn't know what to do with it

---

