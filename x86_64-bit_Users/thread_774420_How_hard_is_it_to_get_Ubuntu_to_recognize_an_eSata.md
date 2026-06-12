---
title: "How hard is it to get Ubuntu to recognize an eSata drive?"
date: 2008-04-29
forum: x86 64-bit Users
---

### Post by ASULutzy on 2008-04-29
With this nice little government cheese check I was thinking about buying some more storage. Was looking at [http://www.newegg.com/Product/Product.aspx?Item=N82E16822216041](http://www.newegg.com/Product/Product.aspx?Item=N82E16822216041) which is a 1 TB eSata/USB 2.0 drive.

Just wondering how tough it is to get this up and running in Hardy 64? Is it pretty much plug and play, maybe with some fstab changes?

I'm 99% sure that using USB shouldn't offer any problems whatsoever, but I've got no experience working with eSata inside of Ubuntu.

Anyone else using an eSata drive with Hardy 64?

---

### Post by cariboo on 2008-04-29
It's completely plug and play. Just make sure its connect when you start your computer and thats it.

JIm

---

### Post by paulisdead on 2008-04-30
> **cariboo907 said:**
> It's completely plug and play. Just make sure its connect when you start your computer and thats it.

JIm

Not necessarily true, depending on the motherboard.  On my Gigabyte P35 mobo, I can hotplug esata drives just fine.  On Intel systems you do have to make sure that AHCI is enabled in the BIOS, but when it is, hotplug works like a champ.

I'm not sure about what other chipsets support hotplug under linux, though.  So I can't vouch for anything besides intel's.

---

### Post by Julius on 2008-04-30
Yup, sata working in AHCI mode should allow hot plug. But if it's not enabled, then it will have to be connected at boot time.

---

### Post by ASULutzy on 2008-04-30
Thanks guys :)

---

### Post by johnnybirdman on 2008-04-30
> **paulisdead said:**
> Not necessarily true, depending on the motherboard.  On my Gigabyte P35 mobo, I can hotplug esata drives just fine.  On Intel systems you do have to make sure that AHCI is enabled in the BIOS, but when it is, hotplug works like a champ.

I'm not sure about what other chipsets support hotplug under linux, though.  So I can't vouch for anything besides intel's.

How do you mount/dismount?  Right now I have an external connected via esata (to my intel board with the proper AHCI settings.)  I can manually mount (sudo mount /dev/sdbx /home/user/xxxxxx) once I power it up but it would be nice if it was auto, like USB.
Any suggestions or ideas??

---

### Post by ASULutzy on 2008-04-30
Try editing /etc/fstab

---

### Post by johnnybirdman on 2008-04-30
> **ASULutzy said:**
> Try editing /etc/fstab

I have been looking at editing fstab for some time but I see issues with auto mount and noauto if the drive is external and not powered on at bootup and/or will be turned off while the system is still running.  Guess I need to look again.  Surprised that in all my searches I can find no definitive guide on setting up esata and fstab.
J.

---

