---
title: "Realtek 8139 problems - 8139cp / 8139too both loading"
date: 2006-05-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by bjtuna on 2006-05-03
installed Breezy on my new computer which is powered by an MSI RS482M4-ILD board. It has a built-in RTL 8139 pci ethernet card.  One of the problems I'm seeing is that both the 8139cp and 8139too modules are being loaded at boot. By playing around with it, I have determined that 8139cp is unnecessary; if I manually remove them both and then load up 8139too, the network works.  So I'm trying to figure out how to get the system to NOT LOAD 8139cp at boot, but my efforts are failing. I've tried adding the module to /etc/hotplug/blacklist but it still gets loaded.  Any ideas?

BTW I have noticed that this is the exact behavior described in the following bug:
[https://lists.ubuntu.com/archives/kernel-bugs/2005-August/002290.html](https://lists.ubuntu.com/archives/kernel-bugs/2005-August/002290.html)

Thanks in advance!

---

### Post by Stormbringer on 2006-05-03
Rather ugly workaround I use myself since I'm using Realtek's kernelmodule for my onboard 8169S ... simply delete the kernel module in question ...

# sudo rm /lib/modules/`uname -r`/kernel/drivers/net/8139cp.ko

... or move it to another place ...

# sudo mv /lib/modules/`uname -r`/kernel/drivers/net/8139cp.ko ~/
   This will move the module into the home directory

Do a ...

# sudo depmod -a

... backup the original initrd just to be safe ...

# sudo cp /boot/initrd.img-`uname -r` /boot/initrd.img-`uname -r`.ubuntu

... rebuild the initrd so that the module won't be included anymore ...

# sudo mkinitramfs -o /boot/initrd.img-`uname -r` `uname -r`

... and you are finished.

If you made no mistakes simply reboot and you should only have 8139too loaded.

Word of WARNING: If you mess things up you may end up with an unbootable system ... be careful!

[EDIT]
In case a kernel-update shows up you need to go through these steps again!
[/EDIT]

Storm.

---

### Post by bjtuna on 2006-05-03
Yuck. I think I'll probably just recompile the kernel with that module omitted.



[QUOTE=Stormbringer]Rather ugly workaround I use myself since I'm using Realtek's kernelmodule for my onboard 8169S ... simply delete the kernel module in question ...

# sudo rm /lib/modules/`uname -r`/kernel/drivers/net/8139cp.ko

... or move it to another place ...

# sudo mv /lib/modules/`uname -r`/kernel/drivers/net/8139cp.ko ~/
   This will move the module into the home directory

Do a ...

# sudo depmod -a

... backup the original initrd just to be safe ...

# sudo cp /boot/initrd.img-`uname -r` /boot/initrd.img-`uname -r`.ubuntu

... rebuild the initrd so that the module won't be included anymore ...

# sudo mkinitramfs -o /boot/initrd.img-`uname -r` `uname -r`

... and you are finished.

If you made no mistakes simply reboot and you should only have 8139too loaded.

Word of WARNING: If you mess things up you may end up with an unbootable system ... be careful!

[EDIT]
In case a kernel-update shows up you need to go through these steps again!
[/EDIT]

Storm.[/QUOTE]

---

