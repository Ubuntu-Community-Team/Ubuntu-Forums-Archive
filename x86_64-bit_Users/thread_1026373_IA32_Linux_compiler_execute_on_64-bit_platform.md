---
title: "IA32 Linux compiler execute on 64-bit platform"
date: 2008-12-31
forum: x86 64-bit Users
---

### Post by gals88 on 2008-12-31
Hi all,
I have downloaded the Arm 2007q1 - 21 release compiler (ARM EABI / IA32 Linux), but cannot execute it...

When trying to execute for e.g:
./arm-none-linux-gnueabi-gcc
I get the message:
bash: ./arm-none-linux-gnueabi-gcc: No such file or directory.

The file has all required permissions.
Could it be related to the fact that the comiler is for 32 bit, and my platform is 64 bit?
If yes, does anyone knows were can I find 64-bit arm 2007q1 compiler?

Thanks
Gal

---

### Post by michael37 on 2009-01-17
Run 

chmod +x ./arm-none-linux-gnueabi-gcc
ldd ./arm-none-linux-gnueabi-gcc

And tell us what u see.

You may need to to run

sudo apt-get install ia32-libs

and try to above process again.

---

