---
title: "How-to: Qemu + Kqemu on Edgy AMD64"
date: 2006-11-03
forum: x86 64-bit Users (Pre April '08)
---

### Post by factor on 2006-11-03
Here is how i got it working on Edgy for AMD64
```

sudo apt-get install qemu build-essential linux-headers-$(uname -r)
wget http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre9.tar.gz
tar xzf kqemu-1.3.0pre9.tar.gz
cd kqemu-1.3.0pre9
./configure --prefix=/usr --disable-gcc-check --kernel-path=/lib/modules/$(uname -r)/build/
make
sudo ./install.sh
sudo depmod
sudo modprobe kqemu
sudo dpkg-reconfigure linux-image-`uname -r`

```

And then, i made a script i run everytime i want to run qemu +kqemu, you have to make an icon for it in your start menu as it is thought to be run in gnome. If you want to run it in terminal replace "gksu" for "sudo":

```

gksu mknod /dev/kqemu c 250 0 
gksu chmod 666 /dev/kqemu
qemu-system-x86_64 -boot c -hda /path/to/your/image.qcow -m 512 -localtime -kernel-kqemu

```

-m 512 is the amount of ram, here is 512 mb, if you want 256 it would be -m 256, and so on.

Hope it helps.

Regards.

---

### Post by slid3r on 2006-11-11
Nice.

---

### Post by Azrael Nightwalker on 2006-11-17
This howto works also for 32-bit version

---

### Post by sureinlux on 2006-11-26
Hi, This works like a charm. Thanks a lot...

---

### Post by The Doc on 2006-12-14
woha, that did work, currently installing win98 :)

This totally rocks, no dual booting for testing some code on windows - thanks!

---

### Post by prashmohan on 2006-12-24
I get this error when I modprobe kqemu

$ sudo modprobe kqemu                                          [...u-1.3.0pre9]
FATAL: Error inserting kqemu (/lib/modules/2.6.15-25-686/misc/kqemu.ko):
Invalid module format


Does anyone know how to solve this or why it occurs?

P.S I am on a 32 bit platform

---

### Post by redmoskito on 2007-01-17
> **prashmohan said:**
> I get this error when I modprobe kqemu

$ sudo modprobe kqemu                                          [...u-1.3.0pre9]
FATAL: Error inserting kqemu (/lib/modules/2.6.15-25-686/misc/kqemu.ko):
Invalid module format


Does anyone know how to solve this or why it occurs?

P.S I am on a 32 bit platform


I received the same error.

Also, when I compiled, I received the warning: 

WARNING: could not find /home/ksimek/download/kqemu-1.3.0pre9/.kqemu-mod.o.cmd for /home/ksimek/download/kqemu-1.3.0pre9/kqemu-mod.o

I'm not sure if this is related

---

### Post by enopepsoo on 2007-01-17
nice one!

I should give this a go sometime and think about ditching vmware.  (Those Bastards).  On the other hand, I really have no incentive to do so... ](*,)

---

### Post by test on 2007-02-13
did someone really test qemu + kqemu on amd64? everytime I boot up a guest it crashes and dmesg shows up the module received a General Protection exception 0x0d

---

### Post by daigidan on 2007-03-25
For those interested in using checkinstall to create a .deb, I was able to get it working on amd64 by replacing the "./install.sh" with the following:

```
checkinstall --exclude=/lib/modules/$(uname -r)/modules.usbmap,/lib/modules/$(uname -r)/modules.alias,/lib/modules/$(uname -r)/modules.ccwmap,/lib/modules/$(uname -r)/modules.dep,/lib/modules/$(uname -r)/modules.ieee1394map,/lib/modules/$(uname -r)/modules.inputmap,/lib/modules/$(uname -r)/modules.isapnpmap,/lib/modules/$(uname -r)/modules.ofmap,/lib/modules/$(uname -r)/modules.pcimap,/lib/modules/$(uname -r)/modules.seriomap,/lib/modules/$(uname -r)/modules.symbols,/lib/modules/$(uname -r)/modules.usbmap
```

This works around errors when the package is installed stating that these files belong to the kernel image package and are trying to be overwritten (I hate force installs). I have no idea if this will vary from system to system. ;]

---

### Post by Konstantin Lvov on 2007-05-04
> **test said:**
> did someone really test qemu + kqemu on amd64? everytime I boot up a guest it crashes and dmesg shows up the module received a General Protection exception 0x0d
Yes, I'm running qemu+kqemu on Athlon x86_64 for several months (on Dapper), and it works fine. But it seems that some conditions must be met:
1) It must be 64-bit Ubuntu version, not 32-bit version installed on 64-bit platform.
2) I built qemu with recommended gcc version (3.4), without --disable-gcc-check option. Pre-built package available from repository doesn't include kqemu accelerator support.
3) In order kqemu accelerator to work, qemu-system-x86_64 binary must be used (not just qemu binary)

---

### Post by explainer on 2007-06-01
This is a cool solution.  Can someone update it for use in a KVM-enabled environment?

---

