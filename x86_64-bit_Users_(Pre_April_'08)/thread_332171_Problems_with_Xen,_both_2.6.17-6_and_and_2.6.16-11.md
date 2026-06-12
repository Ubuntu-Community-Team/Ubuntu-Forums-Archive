---
title: "Problems with Xen, both 2.6.17-6 and and 2.6.16-11.2"
date: 2007-01-05
forum: x86 64-bit Users (Pre April '08)
---

### Post by wigyori on 2007-01-05
Hello,

I'm experiencing problems with Xen, installing from package on an Asus M2N-E with an AMD64 X2 3800+ CPU. This is an nForce 570-based board, which I put an old Matrox VGA card into and 2Gb memory.

With 2.6.16-11.2, the following grub configuration was used:
title           XEN/2.6.16
root            (hd0,1)
kernel          /boot/xen-3.0-amd64.gz noapic
module          /boot/xen0-linux-2.6.16-11.2-generic root=/dev/sda2 ro dom0_mem=262144
module          /boot/initrd.img-2.6.16-11.2
savedefault
boot

The bootup process went fine, however, few seconds after the login prompt appeared, the box froze without any error message. I was thinking that some kernel module which loaded at that time caused the problem, but the same happened with using 'init=/bin/bash' on the kernel command line. I've tried recompiling the kernel with all debug flags enabled, with no usable result at freeze time.

With 2.6.17-6, the following grub configuration was used:
title           XEN/2.6.17
root            (hd0,1)
kernel          /boot/xen-3.0-amd64.gz noapic
module          /boot/xen0-linux-2.6.17-6-generic-xen0 root=/dev/sda2 ro dom0_mem=262144
module          /boot/initrd.img-2.6.17-6-generic
savedefault
boot
This froze after 'Begin: Running /scripts/init-bottom' appeared on the console, again, no usable result after recompiling the kernel with debug flags. When the process reached module installing, some strange errors came up about ".smp_lock", has anyone else seen this?

This seems to be a hardware bug, but since the box runs fine with generic kernels, I would exclude it from here. 

Any hint? (or on how I should debug what causes the freeze?)

Regards,
-w-

---

### Post by wigyori on 2007-01-06
Freeze happens with the original Xen-3.0.3 binary tarball downloaded from their site. I've installed a Dapper also, thinking that the newer libc6 (edgy: 2.4, feisty: 2.5) could have caused the problem, but it was the same.

However, booting the Xen liveCD runs fine, boots up domUs, etc... Could this problem be Ubuntu-related?

---

### Post by wigyori on 2007-01-06
OK, not Ubuntu-specific, rather AMD64-specific, the same happened on a Debian Etch - the Xen liveCD is i386. So, what's up with Xen on nForce5 chipsets?

---

### Post by wigyori on 2007-01-07
Problem solved with a BIOS update, if someone comes along this problem, upgrading to at least BIOS version 0602 is recommended.

---

### Post by beazer on 2007-02-26
That's the closest match I've ever had for looking up a problem - I have an M2N-E mb with AMD X2 3800+ with an old matrox card . . . and I am getting the same lockups.

I'll update the BIOS - thanks for the tip.

---

### Post by beazer on 2007-03-02
Nope.  I upgraded the bios to 0802, and still got a hang after 48 hours or so.  Keyboard and mouse lock up on dom0.  My single domU is still running OK.  I may try downgrading the bios to 0602, or rolling my own dom0 kernel

---

### Post by wigyori on 2007-03-11
You're using the kernel from Ubuntu's package or the original tarball?

---

