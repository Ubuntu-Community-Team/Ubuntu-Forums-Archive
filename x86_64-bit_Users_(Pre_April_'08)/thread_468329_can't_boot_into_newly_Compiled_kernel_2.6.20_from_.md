---
title: "can't boot into newly Compiled kernel 2.6.20 from scratch"
date: 2007-06-08
forum: x86 64-bit Users (Pre April '08)
---

### Post by alimovz on 2007-06-08
Hey guys,

I downloaded the sources from kernel.org for 2.6.20. Ran make xconfig, ran make. bzImage was created, I copied it into the /boot directory as vmlinuz-2.6.20. Then I ran make modules-install which created direcotry /lib/modules/2.6.20 with everything that is supposed to be in there eg modules.dep etc..
 I also made a initrd.img by running mkinitrd -o /boot/initrd.img.
Here is the grub menu.lst lines:
title           2.6.20 Custom Built Kernel
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20 root=/dev/sda3 ro quiet splash
initrd          /boot/initrd.img


When I select this option in the grub menu, an error message shown on the screen after like 10 seconds that says:
Can't open /lib/modules/2.6.20 no such file or directory
can't load /lib/modules/2.6.20/modules.dep no such file or directory
...
...
And so on.

But that directory is there!! make modules-install created it. I checked, the directory exists!! 

Does any one have any ideas? What is wrong there?

Thanks.

---

### Post by kuja on 2007-06-08
I've no idea what could be wrong, but I find it easier to just make a debian package for it usually:

goes something like ...

cp /boot/config-`uname -r` .
make xconfig
make-kpkg clean
fakeroot make-kpkg --initrd --revision=custom.1.0 kernel_image
cd ../
dpkg -i *.deb

---

