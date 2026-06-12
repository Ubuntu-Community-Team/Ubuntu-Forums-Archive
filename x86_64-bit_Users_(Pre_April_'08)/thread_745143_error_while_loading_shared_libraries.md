---
title: "error while loading shared libraries"
date: 2008-04-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by duffstar on 2008-04-04
Hi 

I'm trying to install a scientific software package (ArrayAssist) using a shell script provided by the developers. On a quad core Intel Xeon machine using 64 bit ubuntu 7.10 the installation is failing with the following error:

[FONT="System"]grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.17397/Linux/resource/jre/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory[/FONT]

Could anyone point me in the right direction? I've installed libpthread and the libpthread-dev package but the installer still fails. The developers (Stratagene) are being tardy in getting back to me.

Thanks for any advice.

duff

---

### Post by Kilz on 2008-04-04
> **duffstar said:**
> Hi 

I'm trying to install a scientific software package (ArrayAssist) using a shell script provided by the developers. On a quad core Intel Xeon machine using 64 bit ubuntu 7.10 the installation is failing with the following error:

[FONT="System"]grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.17397/Linux/resource/jre/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory[/FONT]

Could anyone point me in the right direction? I've installed libpthread and the libpthread-dev package but the installer still fails. The developers (Stratagene) are being tardy in getting back to me.

Thanks for any advice.

duff

Odds are its a 32bit application. Start off by installing ia32-libs. After that you can use [getlibs]("http://ubuntuforums.org/showthread.php?t=474790&highlight=getlibs") to install any other libs it needs.

---

### Post by duffstar on 2008-04-04
Hi Kilz,

Great script... :-)

I've installed the ia-32 libs and then looked for the error messages after trying to install ArrayAssist. I then used getlibs with the -l flag to install any libraries flagged by the installer. I still have an error massage! Grr...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.14446/Linux/resource/jre/jre/bin/java: error while loading shared libraries: libpthread.so.0: wrong ELF class: ELFCLASS64

Can you help with this at all?

Thanks again

Iain

---

### Post by Cappy on 2008-04-04
```
sudo apt-get install ia32-libs libc6-i386
```

ia32-libs in there just for anyone else who stumbles upon the thread

---

### Post by duffstar on 2008-04-04
Those are already installed! 

:-(

Thanks though.

Iain

---

### Post by Cappy on 2008-04-04
Well, the script is definitely broken. If you can edit the installation script you may want to look at this thread:
[http://people.debian.org/~terpstra/message/20080206.143106.00ab4066.en.html](http://people.debian.org/~terpstra/message/20080206.143106.00ab4066.en.html)

It may not work under 32-bit either. If somehow it DOES work on 32-bit it would run under a chroot okay.

---

### Post by duffstar on 2008-04-04
Thanks Cappy.

I'll try that out tomorrow or Monday (it's the weekend here now - yipee) and let you now how it goes.

Cheers

Iain

---

