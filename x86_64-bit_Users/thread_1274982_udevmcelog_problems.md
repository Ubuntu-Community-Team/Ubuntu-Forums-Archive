---
title: "udev/mcelog problems"
date: 2009-09-25
forum: x86 64-bit Users
---

### Post by pacetownsley on 2009-09-25
Just installed mcelog on server edition 9.04 and removed /etc/mcelog-disabled. 

There are instructions in /usr/share/doc/mcelog/README.Debian to create /dev/mcelog if you are not running udev. udev is running here. When I run mcelog, I get the message:

 "Cannot open /dev/mcelog"

.. so I stopped udev and created the device as per the instructions in README.Debian: 

mknod /dev/mcelog c 10 227
chown root:root /dev/mcelog
chmod 0660 /dev/mcelog

but I get the same error message from mcelog after creating the device manually:

mcelog --debian-test
/dev/mcelog is NOT usable (No such file or directory)

ls -l /dev/mcelog
crw-rw---- 1 root root 10, 227 2009-09-25 07:18 /dev/mcelog

The message is the same when the device exists and when it doesn't. It also happens when udev is running and when udev is turned off. I don't seem to be able to affect it. 

The docs say "You need to configure your kernel with CONFIG_X86_MCE=y (which
is the default)." This is an untouched stock kernel. 

I'm slightly desperate to fix this because I'm positive there's a hardware problem with the machine. Any suggestions are appreciated.

---

### Post by Mike Uchima on 2009-10-07
I'm having the exact same issue here, on 9.04 desktop edition. The mcelog tool appears to work correctly on a nearly identical system that is running 8.04 LTS instead of 9.04, so this bug was apparently introduced sometime after the 8.04 release. (I don't currently have an 8.10 or 9.10 box set up to see if the problem also exists on those releases.)

My CPU is an AMD Phenom 9550, if that makes a difference.

---

