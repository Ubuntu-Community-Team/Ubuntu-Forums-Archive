---
title: "cant make my custom kernel to work"
date: 2009-04-01
forum: x86 64-bit Users
---

### Post by nvid1a on 2009-04-01
hi there once again, im having a bit of a problem making my custom kernel.

well i used the instructions from this URL on how to make a custom kernel for, in this case, my hp notebook in ubuntu 8.10 x64:

[http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/](http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/)

well it all runs good, my custom config file is done named under nv.config then i run the make-kpkg clean as the tutorial said followed by this line to make the .deb files and my notebook fails, this is the output after this command line:

fakeroot make-kpkg --initrd --append-to-version=-nvid1a kernel_image kernel_headers

root@nvid1a-tablet:/usr/src/linux# make menuconfig
scripts/kconfig/mconf arch/x86/Kconfig
#
# configuration written to nv.config
#


*** End of Linux kernel configuration.
*** Execute 'make' to build the kernel or try 'make help'.

root@nvid1a-tablet:/usr/src/linux# make-kpkg clean
exec debian/rules  DEBIAN_REVISION=5:10.Custom  clean 
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 3: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator

====== making target CLN-common [new prereqs: testdir]======

====== making target CLN-common [new prereqs: ]======
/usr/bin/make -f ./debian/rules real_stamp_clean
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 3: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
make[1]: Entering directory `/usr/src/linux-source-2.6.27'
====== making target real_stamp_clean [new prereqs: ]======
running clean
test ! -f scripts/package/builddeb.kpkg-dist ||                     \
          mv -f scripts/package/builddeb.kpkg-dist scripts/package/builddeb
test ! -f scripts/package/Makefile.kpkg-dist ||                     \
          mv -f scripts/package/Makefile.kpkg-dist scripts/package/Makefile
test ! -f .config  || cp -pf .config config.precious
test ! -f Makefile || \
            /usr/bin/make    ARCH=xen distclean
make[2]: Entering directory `/usr/src/linux-source-2.6.27'
Makefile:528: /usr/src/linux-source-2.6.27/arch/xen/Makefile: No such file or directory
make[2]: *** No rule to make target `/usr/src/linux-source-2.6.27/arch/xen/Makefile'.  Stop.
make[2]: Leaving directory `/usr/src/linux-source-2.6.27'
make[1]: *** [real_stamp_clean] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.27'
make: *** [CLN-common] Error 2
root@nvid1a-tablet:/usr/src/linux# fakeroot make-kpkg --initrd --append-to-version=-nvid1a kernel_image kernel_headers
Warning: The file include/linux/version.h exists
The contained UTS_VERSION string:
			""
does not match expectations:
			"2.6.27.10-nvid1a"
I'll try and recover
exec debian/rules  DEBIAN_REVISION=2.6.27.10-custom-10.00.Custom  APPEND_TO_VERSION=-nvid1a  INITRD=YES  kernel_image kernel_headers 
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 3: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator
[: 1: 2: unexpected operator

====== making target CONFIG-common [new prereqs: testdir]======

====== making target CONFIG-common [new prereqs: stamp-conf]======
This is kernel package version 11.001-0.1.
====== making stamp-arch-conf because of  ======

====== making target CONFIG-arch [new prereqs: stamp-arch-conf]======
====== making target conf.vars [new prereqs: Makefile .config]======

Makefile:528: /usr/src/linux-source-2.6.27/arch/xen/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-source-2.6.27/arch/xen/Makefile'.  Stop.
make: *** [conf.vars] Error 2

i will appreciate any help, maybe it is something i miss, dont know.

thanks!

---

### Post by Yellow Pasque on 2009-04-02
Disable the Xen/paravirtualization stuff under the "Processor Type and Features" submenu (unless you're trying to build a kernel to run xen).

---

