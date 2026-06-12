---
title: "compiling wine"
date: 2006-10-29
forum: x86 64-bit Users (Pre April '08)
---

### Post by xstaticxgpx on 2006-10-29
I'm trying to compile wine on 64 bit edgy, i followed the directions from [here]("http://wiki.winehq.org/WineOn64bit") but after doing make depend && make i run into a error about "elf64 to format elf32"

> 
ld: Relocatable linking with relocations from format elf64-x86-64 (/usr/lib/libsicuuc.a(ubidi.ao)) to format elf32-i386 (gdi32.4wBzBt.o) is not supported
winebuild: ld -m elf_i386 -r failed with status 256
winegcc: ../../tools/winebuild/winebuild failed.
make[2]: *** [gdi32.dll.so] Error 2


if anyone can give me any help with this it'd be greatly appreciated.

---

### Post by nielz on 2006-10-29
If you don't really need to compile wine, you could also use the the install script supplied in [Install 32 bit wine to 64 bit Dapper without chroot]("http://www.ubuntuforums.org/showthread.php?t=185557"). Though the topic says Dapper it works fine on Edgy as well.

---

### Post by xstaticxgpx on 2006-10-29
yea, thats what i eventually resorted to, I'd still like to have a 64bit optimized version of wine though.

---

### Post by RAOF on 2006-10-29
> **xstaticxgpx said:**
> yea, thats what i eventually resorted to, I'd still like to have a 64bit optimized version of wine though.

**You can't**.  You're trying to run 32bit Windows code, so Wine needs to be 32bit also.

Ok, you **can** compile Wine as a 64bit binary.  Then it will (possibly - the support is very new) run Win64 programs (only), which you can count on the fingers of one foot.

---

