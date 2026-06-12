---
title: "Compiling/installing kernel using make-kpkg on 8.10 amd64"
date: 2008-11-15
forum: x86 64-bit Users
---

### Post by eraserix on 2008-11-15
Hello

Recently I tried to compile a kernel on Ubuntu 8.10 and it wasn't as straightforward as I'd expect. The problem seems to be coming from make-kpkg; there were no problems with normal make clean.

The following steps reproduce the problem on my amd64 ubuntu 8.10:
[LIST=1]
[*]sudo aptitude install linux-source-2.6.27
[*]cd /usr/src/
[*]tar -xjf linux-source-2.6.27.tar.bz2
[*]ln -s linux-source-2.6.27 linux
[*]cd linux
[*]cp /boot/config-2.6.27-7-generic .config
[*]make-kpkg clean
[/LIST]

I get the following output:
```

exec make -f /usr/share/kernel-package/ruleset/minimal.mk clean 
====== making target minimal_clean [new prereqs: ]======
Cleaning.
test ! -f .config || cp -pf .config config.precious
test ! -e stamp-building || rm -f stamp-building
test ! -f Makefile || \
            make    ARCH=xen distclean
make[1]: Entering directory `/home/chrigu/Work/linux-source-2.6.27'
Makefile:528: /home/chrigu/Work/linux-source-2.6.27/arch/xen/Makefile: No such file or directory
make[1]: *** No rule to make target `/home/chrigu/Work/linux-source-2.6.27/arch/xen/Makefile'.  Stop.
make[1]: Leaving directory `/home/chrigu/Work/linux-source-2.6.27'
make: *** [minimal_clean] Error 2

```

'make clean' works fine however. After commenting out CONFIG_XEN=y, the kernel compiles through. When I try to install the new package, I get an error on 'run-parts: executing /etc/kernel/postinst.d/nvidia-common' about non-zero returncode. Adding 'exit 0' at the end of the script nvidia-common and removing the -e parameter to bash on the first line lets me install the kernel without problems.

Cheers,
Christoph

---

### Post by JBauer5 on 2008-12-27
I'm having the same problem in xubuntu, if anyone knows how to fix this It'd be much appreciated.

The problem seems to stem from copying over my old config files then trying to build:

> sudo cp /boot/config-`uname -r` ./.config
sudo make-kpkg clean

And I get a similar error:
> exec make -f /usr/share/kernel-package/ruleset/minimal.mk clean 
====== making target minimal_clean [new prereqs: ]======
Cleaning.
test ! -f .config || cp -pf .config config.precious
test ! -e stamp-building || rm -f stamp-building
test ! -f Makefile || \
            make    ARCH=xen distclean
make[1]: Entering directory `/usr/src/linux-source-2.6.27'
Makefile:528: /usr/src/linux-source-2.6.27/arch/xen/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-source-2.6.27/arch/xen/Makefile'.  Stop.
make[1]: Leaving directory `/usr/src/linux-source-2.6.27'
make: *** [minimal_clean] Error 2


Update: I've fixed the problem by running: 'make xconfig' instead, but now I've run into a different problem.  I'm having problems with the next step in compiling my new kernel.

When I try

> sudo fakeroot make-kpkg - -initrd - -append-to-version=-injection kernel_image kernel_headers

or 

CONCURRENCY_LEVEL=3 make-kpkg --initrd --revision=386 kernel_image 
kernel_headers modules_image

I get the error
> Error: Unknown target - Unknown target - 
use --targets to display help on valid targets.


---

