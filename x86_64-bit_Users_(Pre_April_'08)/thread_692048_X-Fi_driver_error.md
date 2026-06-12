---
title: "X-Fi driver error"
date: 2008-02-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by deadi on 2008-02-09
Hi all, I am trying to get the X-Fi card working in Ubuntu Gutsy and not having much luck.
can someone help with this error?

make[2]: *** No rule to make target `arch/x86_64/kernel/asm-offsets.c', needed by `arch/x86_64/kernel/asm-offsets.s'.  Stop.

This is after the comand:
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

Doing these instructions:

[http://ubuntuforums.org/showthread.php?t=571656&highlight=xfi&page=5](http://ubuntuforums.org/showthread.php?t=571656&highlight=xfi&page=5)

The only other drivers installed are the Envy Nvidia drivers. Other then that, this is a fresh install.

Oh, Ive also tried the OSS alsa driver without much luck. My previous install of Gutsy and the creative drivers worked.

Oh, I wont be buying another creative product ............

---

### Post by NullHead on 2008-02-09
Ok I've had this problem before ... (not quite sure what causes it) but I did get around it. do ```
sudo make clean
``` and then start over with the coying the .conf and make-kpkg clean .etc

---

### Post by deadi on 2008-02-09
I get the same thing:

make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CHK     include/linux/version.h
  UPD     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86_64
make[2]: *** No rule to make target `arch/x86_64/kernel/asm-offsets.c', needed by `arch/x86_64/kernel/asm-offsets.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [debian/stamp-kernel-conf] Error 2

What is no rule to make target?

EDIT Ok i found this:
rule to make target `xxx', needed by `yyy'.'
    This means that make decided it needed to build a target, but then couldn't find any instructions in the makefile on how to do that, either explicit or implicit (including in the default rules database). If you want that file to be built, you will need to add a rule to your makefile describing how that target can be built. Other possible sources of this problem are typos in the makefile (if that filename is wrong) or a corrupted source tree (if that file is not supposed to be built, but rather only a dependency).

---

### Post by deadi on 2008-02-09
There are 2 people on the forums that i have found with no resolution:

 Originally Posted by kerozion  View Post
Everything was going well until compiling and this came up in the first 2 minutes:

make[2]: *** No rule to make target `arch/x86_64/kernel/asm-offsets.c', needed by `arch/x86_64/kernel/asm-offsets.s'. Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [debian/stamp-kernel-conf] Error 2


Any ideas?

I've no idea as I'm not a very sophisticated user. It would be easier to buy a new scound card but I can't based on the principle.

Any help would be great.

---

### Post by NullHead on 2008-02-09
Ok well it looks like you download the kernel source from synaptic? If so I would download the suggested kernel from my guide, 2.6.22-10. I also sounds like you have a corrupt source tree ... in short it sounds like it didn't download correctly.

Look at the content of /usr/src ```
sudo ls -A /usr/src/
``` and remove you're old kernel ```
sudo rm -rf <kernel directory>
``` unpack it again.```
tar xjf linux-2.6.22.10.tar.bz2
```

---

### Post by deadi on 2008-02-10
I will try it with the older source. I thought I would be able to use the .14 source by changing the instructions accordingly.
I did follow some of the symlinks and discovered that a few are broken, lead to nowhere.

It seems to me linux tends to use a lot of these instead of just looking in a directory normally with the complete path when it needs a file. I do not want to be a critic but I just cant see a valid reason to use symlinks so heavily. It just adds to the confusion and lengthens the learning curve.

How does one go about fixing symlinks? Is there a command that will list all? Or better yet, list and check each one for a valid link?

---

### Post by deadi on 2008-02-10
Heh, I removed all the kernels and symlinks from the /usr/src/ directory, downloaded and tried it with the linux-2.6.22.10.tar.bz2. Its now compiling. Strange, some of the symlinks would not delete. I tried removing the kernels via command line and the same thing, they wouldn't delete. I fired up nautilus using a sudo -i, and they deleted fine. One of the symlinks would not go away until after I renamed it. A refresh problem?

---

### Post by deadi on 2008-02-10
Ok, it finished without error but it came up with this While installing the packages:

Setting up linux-image-2.6.22.14-custom (2.6.22.14-custom-10.00.Custom) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
find: /lib/firmware/2.6.22.14-custom: No such file or directory
find: /lib/firmware/2.6.22.14-custom: No such file or directory
find: /lib/firmware/2.6.22.14-custom: No such file or directory
find: /lib/firmware/2.6.22.14-custom: No such file or directory
find: /lib/firmware/2.6.22.14-custom: No such file or directory
find: /lib/firmware/2.6.22.14-custom: No such file or directory
Running postinst hook script update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22.14-custom
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms

---

### Post by NullHead on 2008-02-10
It installed OK .. restart the computer and boot with the new kernel that should be in your grub listing. Then continue with the installation process.

---

### Post by iumentum on 2008-03-03
> **deadi said:**
> Hi all, I am trying to get the X-Fi card working in Ubuntu Gutsy and not having much luck.
can someone help with this error?

make[2]: *** No rule to make target `arch/x86_64/kernel/asm-offsets.c', needed by `arch/x86_64/kernel/asm-offsets.s'.  Stop.

This is after the comand:
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers

Doing these instructions:

[http://ubuntuforums.org/showthread.php?t=571656&highlight=xfi&page=5](http://ubuntuforums.org/showthread.php?t=571656&highlight=xfi&page=5)

The only other drivers installed are the Envy Nvidia drivers. Other then that, this is a fresh install.

Oh, Ive also tried the OSS alsa driver without much luck. My previous install of Gutsy and the creative drivers worked.

Oh, I wont be buying another creative product ............

Another approach to fix this error, I used a different directory than Linux. I had taken a look into that directory and noticed the default kernel and some other stuff were in there that were mucking the make up. So instead I un-tared to 'newkernel' as my directory name instead of linux. it went fine after that.

---

