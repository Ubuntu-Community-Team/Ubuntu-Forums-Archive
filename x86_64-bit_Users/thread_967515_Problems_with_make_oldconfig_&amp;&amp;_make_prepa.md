---
title: "Problems with make oldconfig &amp;&amp; make prepare' on kernel src [NIST Net installation]"
date: 2008-11-02
forum: x86 64-bit Users
---

### Post by Janek Kowalik on 2008-11-02
Hi
I want to install NIST Net (WAN emulator) and have some problems not necessarily linked with application itself.
When I run 'make' command (first './configure' naturally ) I get following error:
 
```

make[2]: Entering directory `/usr/local/nistnet-3.0a/monitor/Frame-1.0'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/usr/local/nistnet-3.0a/monitor/Frame-1.0'
make[1]: Leaving directory `/usr/local/nistnet-3.0a/monitor'
make[1]: Entering directory `/usr/local/nistnet-3.0a/kernel'
make -C /lib/modules/2.6.24-21-generic/build M=/usr/local/nistnet-3.0a/kernel V=1
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || ( \
echo; \
echo " ERROR: Kernel configuration is invalid."; \
echo " include/linux/autoconf.h or include/config/auto.conf are missing."; \
echo " Run 'make oldconfig && make prepare' on kernel src to fix it."; \
echo; \
/bin/false)
mkdir -p /usr/local/nistnet-3.0a/kernel/.tmp_versions ; rm -f /usr/local/nistnet-3.0a/kernel/.tmp_versions/*
make -f scripts/Makefile.build obj=/usr/local/nistnet-3.0a/kernel
scripts/Makefile.build:46: *** CFLAGS was changed in "/usr/local/nistnet-3.0a/kernel/Makefile". Fix it to use EXTRA_CFLAGS. Stop.
make[2]: *** [_module_/usr/local/nistnet-3.0a/kernel] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/local/nistnet-3.0a/kernel'
make: *** [sub_dirs] Error 2

```

Therefore as it says I run

'make oldconfig && make prepare' on kernel src

However it throws another error which I don't know how to overcome:

```

*
* Library routines
*
CRC-CCITT functions (CRC_CCITT) [M/y/?] m
CRC16 functions (CRC16) [M/y/?] m
CRC ITU-T V.41 functions (CRC_ITU_T) [M/y/?] m
CRC32 functions (CRC32) [Y/?] y
CRC7 functions (CRC7) [M/y/?] m
CRC32c (Castagnoli, et al) Cyclic Redundancy-Check (LIBCRC32C) [M/y/?] m
#
# configuration written to .config
#
scripts/kconfig/conf -s arch/x86/Kconfig

*** Error during writing of the kernel configuration.

make[2]: *** [silentoldconfig] Error 1
make[1]: *** [silentoldconfig] Error 2
make: *** No rule to make target `include/config/auto.conf', needed by `include/config/kernel.release'. Stop.

```

Can anyone help me, please?
I use :
 Ubuntu : Release 8.04 (hardy)
 Kernel Linux 2.6.24-21-generic

Thanks in advance.

---

### Post by TauriDundee on 2008-11-11
I'm having similar problems.... I've been reliably informed that it's much easier to install nistnet on kernel 2.4.x

If anyone know how to install nistnet on any 2.6.x kernel I would love to hear how..... I've tried everything I can find on the net and am at a loss.... please help!

---

