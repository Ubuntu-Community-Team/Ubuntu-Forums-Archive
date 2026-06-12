---
title: "I/O errors, Inconsistency detected etc. ..."
date: 2009-10-26
forum: x86 64-bit Users
---

### Post by gocek on 2009-10-26
Hello,

I'm using Ubuntu 9.04 AMD64 on Asus N51Vf notebook. I've been also using ubuntu 64bit on my desktop for a few years actually (upgrading to newer versions when they were available) with no real issues.
But my experience with ubuntu on the notebook is simply terrible.
I couldn't install it properly, without getting some wierd "errno I/O error" errors (I don't remember the exact name unfortunatelly). I only managed to successfully install the system, when I took one RAM dice out :o (had 2x2GB, worked with 1x2GB).

But even with ubuntu installed on my HDD, the problems were not gone. I keep getting various errors while using Synaptic like:

```
synaptic[4956]: segfault at 7fffb5360ff8 ip 00007fffbed495c4 sp 00007fffb5361000 error 7 in ld-2.9.so[7fffbed3a000+20000]
```

or 

original:
```
Rozpakowanie pakietu zast&#281;puj&#261;cego amarok ...
dpkg: b&#322;&#261;d przetwarzania /var/cache/apt/archives/amarok_2%3a2.0.2mysql5.1.30-0ubuntu3_amd64.deb (--unpack):
 uszkodzone archiwum tar - uszkodzone archiwum pakietu
```
translated Polish->English:
```
Unpacking package to replace amarok ...
dpkg: error while processing /var/cache/apt/archives/amarok_2%3a2.0.2mysql5.1.30-0ubuntu3_amd64.deb (--unpack):
 corrupted archive tar - corrupted package archive
```


And also pretty random errors when I try to launch some applications like amarok or firefox:
```
Inconsistency detected by ld.so: ../sysdeps/x86_64/dl-machine.h: 458: elf_machine_rela_relative: Assertion `((reloc->r_info) & 0xffffffff) == 8' failed!
firefox died with exit status 127
```

I believe it's not my RAM (ran memcheck) and neither my HDD (Vista working flawlessly on another partition).

There're also a few people who have similar problems. There's usually only one solution: to reboot. But for heaven's sake - something's is so wrong with that 64bit version and s[ecific hardware...

Links to similar threads:
[first]("http://ubuntuforums.org/showthread.php?t=822685")
[second]("http://ubuntuforums.org/showthread.php?t=1182346")
[third]("http://ubuntuforums.org/showthread.php?t=1180294")

So my main question is: are the dev team people aware of this issue? And if not, what would be a good place to let them know?
Oh and maybe there's a fix for all this?

If someone has/had similar problems, could you please post if other versions of ubuntu (maybe 32 bit? maybe KDE?) work? And what about other distributions?

---

