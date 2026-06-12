---
title: "latest nvidia"
date: 2005-03-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by AndersAA on 2005-03-13
can't seem to install it on updated hoary, get this:

```

   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.10-4-amd64-k8/build SUBDIRS
   =/root/X/NVIDIA-Linux-x86-1.0-7167-pkg1/usr/src/nv modules
   mkdir -p /root/X/NVIDIA-Linux-x86-1.0-7167-pkg1/usr/src/nv/.tmp_versions
   make -f scripts/Makefile.build obj=/root/X/NVIDIA-Linux-x86-1.0-7167-pkg1/us
   r/src/nv
   echo \#define NV_COMPILER \"`cc -v 2>&1 | tail -n 1`\" > /root/X/NVIDIA-Linu
   x-x86-1.0-7167-pkg1/usr/src/nv/nv_compiler.h
     cc -Wp,-MD,/root/X/NVIDIA-Linux-x86-1.0-7167-pkg1/usr/src/nv/.nv.o.d -nost
   dinc -iwithprefix include -D__KERNEL__ -Iinclude  -Wall -Wstrict-prototypes
   -Wno-trigraphs -fno-strict-aliasing -fno-common -O2     -fomit-frame-pointer
    -mno-red-zone -mcmodel=kernel -pipe -fno-reorder-blocks      -Wno-sign-compare
   -fno-asynchronous-unwind-tables   -I/root/X/NVIDIA-Linux-x86-1.0-7167-pkg1/u
   sr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts
   -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror -O -fno-common -MD
   -Wsign-compare -Wno-cast-qual -Wno-error -D_LOOS
   E_KERNEL_NAMES -D__KERNEL__ -DMODULE  -DNTRM -D_GNU_SOURCE -D_LOOSE_KERNEL_N
   AMES -D__KERNEL__ -DMODULE  -DNV_MAJOR_VERSION=1 -DNV_MINOR_VERSION=0 -DNV_P
   ATCHLEVEL=7167  -DNV_UNIX   -DNV_LINUX   -DNV_INT64_OK   -DNVCPU_X86      -U
   DEBUG -U_DEBUG -DNDEBUG -DNV_SIGNAL_STRUCT_RLIM -DNV_REMAP_PFN_RANGE_PRESENT
   -DNV_CHANGE_PAGE_ATTR_PRESENT -DNV_PCI_DISABLE_DEVICE_PRESENT -DNV_CLASS_SIM
   PLE_CREATE_PRESENT -DNV_PCI_GET_CLASS_PRESENT -DNV_VMAP_4_PRESENT  -DMODULE
   -DKBUILD_BASENAME=nv -DKBUILD_MODNAME=nvidia -c -o /root/X/NVIDIA-Linux-x86-
   1.0-7167-pkg1/usr/src/nv/.tmp_nv.o /root/X/NVIDIA-Linux-x86-1.0-7167-pkg1/us
   r/src/nv/nv.c
   In file included from include/linux/sched.h:15,
                    from include/linux/module.h:10,
                    from /root/X/NVIDIA-Linux-x86-1.0-7167-pkg1/usr/src/nv/nv-l
   inux.h:46,
                    from /root/X/NVIDIA-Linux-x86-1.0-7167-pkg1/usr/src/nv/nv.c
   :14:
   include/linux/cpumask.h: In function `__first_cpu':
   include/linux/cpumask.h:211: warning: signed and unsigned type in conditiona
   l expression
   include/linux/cpumask.h: In function `__next_cpu':
   include/linux/cpumask.h:217: warning: signed and unsigned type in conditiona
   l expression
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:23,
                    from include/asm/semaphore.h:42,
                    from include/linux/sched.h:18,
                    from include/linux/module.h:10,
                    from /root/X/NVIDIA-Linux-x86-1.0-7167-pkg1/usr/src/nv/nv-l
   inux.h:46,
                    from /root/X/NVIDIA-Linux-x86-1.0-7167-pkg1/usr/src/nv/nv.c
   :14:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:837,
                    from /root/X/NVIDIA-Linux-x86-1.0-7167-pkg1/usr/src/nv/nv-l
   inux.h:69,
                    from /root/X/NVIDIA-Linux-x86-1.0-7167-pkg1/usr/src/nv/nv.c
   :14:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:317: warning: wrong type argument to increment
   In file included from include/asm/pci.h:95,
                    from include/linux/pci.h:877,
                    from /root/X/NVIDIA-Linux-x86-1.0-7167-pkg1/usr/src/nv/nv-l
   inux.h:69,
                    from /root/X/NVIDIA-Linux-x86-1.0-7167-pkg1/usr/src/nv/nv.c
   :14:
   include/asm-generic/pci-dma-compat.h: In function `pci_map_page':
   include/asm-generic/pci-dma-compat.h:49: warning: pointer of type `void *' u
   sed in arithmetic
   {standard input}: Assembler messages:
   {standard input}:930: Error: suffix or operands invalid for `mov'
   {standard input}:938: Error: suffix or operands invalid for `mov'
   {standard input}:967: Error: suffix or operands invalid for `mov'
   {standard input}:991: Error: suffix or operands invalid for `mov'
   {standard input}:999: Error: suffix or operands invalid for `mov'
   {standard input}:1025: Error: suffix or operands invalid for `mov'
   /root/X/NVIDIA-Linux-x86-1.0-7167-pkg1/usr/src/nv/nv.c: In function `nv_allo
   c_pages':
   /root/X/NVIDIA-Linux-x86-1.0-7167-pkg1/usr/src/nv/nv.c:2743: warning: cast t
   o pointer from integer of different size
   make[3]: *** [/root/X/NVIDIA-Linux-x86-1.0-7167-pkg1/usr/src/nv/nv.o] Error
   1
   make[2]: *** [_module_/root/X/NVIDIA-Linux-x86-1.0-7167-pkg1/usr/src/nv] Err
   or 2
   NVIDIA: left KBUILD.
   nvidia.ko failed to build!
   make[1]: *** [module] Error 1
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```

---

### Post by c_dog on 2005-03-14
A few questions;
How and where are you trying to run the script from? And do you have the kernel sources in your /usr/src directory? Hoary doesn't install them automatically by default. Be sure the uninstall the 6229 glx files before you compile 7167, also.

c_dog

---

### Post by AndersAA on 2005-03-15
solved it now, had the x86 driver instead of x86_64 :p, this is what I get for working on it in the middle of the night huh ;)

just didn't wanna bump the thread for no reason ;)

---

