---
title: "Boot error after kernel update or no splash"
date: 2006-04-15
forum: x86 64-bit Users (Pre April '08)
---

### Post by jantonio.martin on 2006-04-15
After updating the kernel image to linux-image-2.6.15-20-powerpc in an iBook G4, the system does not boot because of this [bug]("https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/32123").
Booting a previous kernel, I could create a new initrd.img-2.6.15-20-powerpc file in /boot, using mkinitrd. However, with this new initrd.img the framebuffer bootsplash (usplash) does not work. I know that using dpkg-reconfigure linux-image-2.6.15-20-powerpc usplash works again, but then the system won't boot. Also, I think that I could get usplash working again using mkinitrd, but I don't know how. I have looked for it in the forums, man pages, and google, but I haven't found any clues.

---

