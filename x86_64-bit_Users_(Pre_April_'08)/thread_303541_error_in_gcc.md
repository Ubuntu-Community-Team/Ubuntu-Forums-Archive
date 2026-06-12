---
title: "error in gcc  ?"
date: 2006-11-20
forum: x86 64-bit Users (Pre April '08)
---

### Post by costinc on 2006-11-20
When compiling  kernel 2.6.16.32 , from kernel.org following error appear:
```

  CHK     include/linux/compile.h
  UPD     include/linux/compile.h
  CC      init/version.o
  LD      init/built-in.o
  LD      .tmp_vmlinux1
init/built-in.o: In function `try_name':
do_mounts.c:(.text+0x5d5): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `name_to_dev_t':
(.text+0x8a4): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `change_floppy':
(.init.text+0x832): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `mount_block_root':
(.init.text+0xa98): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `do_header':
initramfs.c:(.init.text+0x4001): undefined reference to `__stack_chk_fail'
arch/x86_64/kernel/built-in.o:(.text+0x3509): more undefined references to `__stack_chk_fail' follow
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/home/costin/linux-2.6.16.32'
make: *** [debian/stamp-build-kernel] Error 2

```

Same type of error appear at xen compilation , from 3.0.2 version to unstable .
[SIZE="4"][INDENT]
[COLOR="Red"] undefined reference to `__stack_chk_fail'  [/COLOR]
[/INDENT][/SIZE]

Could be bug in gcc 64 version of Edgy ?

```

gcc -O2 -fomit-frame-pointer -DNDEBUG -m64 -Wall -Wstrict-prototypes
-Wdeclaration-after-statement -nostdinc -fno-builtin -fno-common
-fno-strict-aliasing -iwithprefix include -Werror -Wno-pointer-arith
-pipe -I/home/test1/xen-unstable/xen/include
-I/home/test1/xen-unstable/xen/include/asm-x86/mach-generic
-I/home/test1/xen-unstable/xen/include/asm-x86/mach-default
-msoft-float -mno-red-zone -fpic -fno-reorder-blocks
-fno-asynchronous-unwind-tables -DGCC_HAS_VISIBILITY_ATTRIBUTE -g
-D__XEN__ -c mm.c -o mm.o
gcc -O2 -fomit-frame-pointer -DNDEBUG -m64 -Wall -Wstrict-prototypes
-Wdeclaration-after-statement -nostdinc -fno-builtin -fno-common
-fno-strict-aliasing -iwithprefix include -Werror -Wno-pointer-arith
-pipe -I/home/test1/xen-unstable/xen/include
-I/home/test1/xen-unstable/xen/include/asm-x86/mach-generic
-I/home/test1/xen-unstable/xen/include/asm-x86/mach-default
-msoft-float -mno-red-zone -fpic -fno-reorder-blocks
-fno-asynchronous-unwind-tables -DGCC_HAS_VISIBILITY_ATTRIBUTE -g
-D__XEN__ -c traps.c -o traps.o
ld   -m elf_x86_64 -r -o built_in.o entry.o mm.o traps.o
make[6]: Leaving directory `/home/test1/xen-unstable/xen/arch/x86/x86_64'
ld   -m elf_x86_64 -r -o built_in.o apic.o bitops.o compat.o delay.o
dmi_scan.o domctl.o domain.o domain_build.o e820.o extable.o
flushtlb.o platform_hypercall.o i387.o i8259.o io_apic.o irq.o
microcode.o mm.o mpparse.o nmi.o physdev.o rwlock.o setup.o shutdown.o
smp.o smpboot.o string.o sysctl.o time.o trampoline.o traps.o
usercopy.o x86_emulate.o acpi/built_in.o cpu/built_in.o
genapic/built_in.o hvm/built_in.o mm/built_in.o oprofile/built_in.o
x86_64/built_in.o
make[5]: Leaving directory `/home/test1/xen-unstable/xen/arch/x86'
gcc -O2 -fomit-frame-pointer -DNDEBUG -m64 -Wall -Wstrict-prototypes
-Wdeclaration-after-statement -nostdinc -fno-builtin -fno-common
-fno-strict-aliasing -iwithprefix include -Werror -Wno-pointer-arith
-pipe -I/home/test1/xen-unstable/xen/include
-I/home/test1/xen-unstable/xen/include/asm-x86/mach-generic
-I/home/test1/xen-unstable/xen/include/asm-x86/mach-default
-msoft-float -mno-red-zone -fpic -fno-reorder-blocks
-fno-asynchronous-unwind-tables -DGCC_HAS_VISIBILITY_ATTRIBUTE -g
-D__XEN__ -P -E -Ui386 -D__ASSEMBLY__ -o xen.lds x86_64/xen.lds.S
ld   -m elf_x86_64 -T xen.lds -N \
           boot/x86_64.o
/home/test1/xen-unstable/xen/common/built_in.o
/home/test1/xen-unstable/xen/drivers/built_in.o
/home/test1/xen-unstable/xen/arch/x86/built_in.o -o
/home/test1/xen-unstable/xen/xen-syms
/home/test1/xen-unstable/xen/common/built_in.o: In function `do_domctl':
/home/test1/xen-unstable/xen/common/domctl.c:656: undefined reference
to `__stack_chk_fail'
/home/test1/xen-unstable/xen/common/domctl.c:656: relocation truncated
to fit: R_X86_64_PLT32 against undefined symbol `__stack_chk_fail'
/home/test1/xen-unstable/xen/common/built_in.o: In function `cmdline_parse':
/home/test1/xen-unstable/xen/common/kernel.c:84: undefined reference
to `__stack_chk_fail'
/home/test1/xen-unstable/xen/common/kernel.c:84: relocation truncated
to fit: R_X86_64_PLT32 against undefined symbol `__stack_chk_fail'
/home/test1/xen-unstable/xen/common/built_in.o: In function `do_xen_version':
/home/test1/xen-unstable/xen/common/kernel.c:230: undefined reference
to `__stack_chk_fail'
/home/test1/xen-unstable/xen/common/kernel.c:230: relocation truncated
to fit: R_X86_64_PLT32 against undefined symbol `__stack_chk_fail'
/home/test1/xen-unstable/xen/common/built_in.o: In function `dump_domains':
/home/test1/xen-unstable/xen/common/keyhandler.c:189: undefined
reference to `__stack_chk_fail'
/home/test1/xen-unstable/xen/common/keyhandler.c:189: relocation
truncated to fit: R_X86_64_PLT32 against undefined symbol
`__stack_chk_fail'
/home/test1/xen-unstable/xen/common/built_in.o: In function `__print_symbol':
/home/test1/xen-unstable/xen/common/symbols.c:158: undefined reference
to `__stack_chk_fail'
/home/test1/xen-unstable/xen/common/symbols.c:158: relocation
truncated to fit: R_X86_64_PLT32 against undefined symbol
`__stack_chk_fail'
/home/test1/xen-unstable/xen/common/built_in.o:/home/test1/xen-unstable/xen/common/sysctl.c:142:
more undefined references to `__stack_chk_fail' follow
/home/test1/xen-unstable/xen/common/built_in.o: In function `do_sysctl':
/home/test1/xen-unstable/xen/common/sysctl.c:142: relocation truncated
to fit: R_X86_64_PLT32 against undefined symbol `__stack_chk_fail'
/home/test1/xen-unstable/xen/common/built_in.o: In function `number':
/home/test1/xen-unstable/xen/common/vsprintf.c:242: relocation
truncated to fit: R_X86_64_PLT32 against undefined symbol
`__stack_chk_fail'
/home/test1/xen-unstable/xen/drivers/built_in.o: In function `do_console_io':
/home/test1/xen-unstable/xen/drivers/char/console.c:275: relocation
truncated to fit: R_X86_64_PLT32 against undefined symbol
`__stack_chk_fail'
/home/test1/xen-unstable/xen/drivers/built_in.o: In function `panic':
/home/test1/xen-unstable/xen/drivers/char/console.c:648: relocation
truncated to fit: R_X86_64_PLT32 against undefined symbol
`__stack_chk_fail'
/home/test1/xen-unstable/xen/arch/x86/built_in.o: In function
`__context_switch':
/home/test1/xen-unstable/xen/arch/x86/domain.c:703: relocation
truncated to fit: R_X86_64_PLT32 against undefined symbol
`__stack_chk_fail'
/home/test1/xen-unstable/xen/arch/x86/built_in.o: In function `do_platform_op':
/home/test1/xen-unstable/xen/arch/x86/platform_hypercall.c:149:
additional relocation overflows omitted from the output
make[4]: *** [/home/test1/xen-unstable/xen/xen-syms] Error 1
make[4]: Leaving directory `/home/test1/xen-unstable/xen/arch/x86'
make[3]: *** [/home/test1/xen-unstable/xen/xen] Error 2
make[3]: Leaving directory `/home/test1/xen-unstable/xen'
make[2]: *** [install] Error 2
make[2]: Leaving directory `/home/test1/xen-unstable/xen'
make[1]: *** [install-xen] Error 2
make[1]: Leaving directory `/home/test1/xen-unstable'
make: *** [world] Error 2

```
System is ubuntu-edgy , gcc version
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v
--enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr
--enable-shared --with-system-zlib --libexecdir=/usr/lib
--without-included-gettext --enable-threads=posix --enable-nls
--program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu
--enable-libstdcxx-debug --enable-mpfr --enable-checking=release
x86_64-linux-gnu
Thread model: posix
gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)

---

### Post by tgal on 2006-11-24
Put a "-fno-stack-protector" into CFLAGS in toplevel Config.mk!

---

### Post by genibot on 2006-12-08
I tried this, but I still get the same error when compiling Xen.  Has anyone else solved this?

---

### Post by magick- on 2006-12-12
Did you 'make clean'?

Tom Groves

---

### Post by alben on 2006-12-12
> **genibot said:**
> I tried this, but I still get the same error when compiling Xen.  Has anyone else solved this?

Yes and it was a long try-and-error way on a slow system ;)

_**Compiling Xen 3.0.3 from Source**_

1) try to build Xen at least once: 
```

#cd xen-3.0.3_0-src/
#make world

```2) add *-fno-stack-protector* to CFLAGS in these files:
```

#vi Config.mk                          # near line 36
#vi pristine-linux-2.6.16.29/Makefile  # near line 342
#vi ref-linux-2.6.16.29/Makefile       # this should be hardlinked to the files above
#vi linux-2.6.16.29-xen/Makefile       # this should be hardlinked to the files above

```I hope that will help. If not try to do a *#ls -lrt* after the error occurs. In the bottom section you'll get an idea which other linux source directories you have to edit.

[Here]("http://www.howtoforge.com/debian_sarge_xen_3.0.3_p2") is a nice tutorial how to build dedicated Xen0 and XenU kernels

---

### Post by skibrianski on 2007-01-10
> **alben said:**
> Yes and it was a long try-and-error way on a slow system ;)

_**Compiling Xen 3.0.3 from Source**_

1) try to build Xen at least once: 
```

#cd xen-3.0.3_0-src/
#make world

```2) add *-fno-stack-protector* to CFLAGS in these files:
```

#vi Config.mk                          # near line 36
#vi pristine-linux-2.6.16.29/Makefile  # near line 342
#vi ref-linux-2.6.16.29/Makefile       # this should be hardlinked to the files above
#vi linux-2.6.16.29-xen/Makefile       # this should be hardlinked to the files above

```I hope that will help. If not try to do a *#ls -lrt* after the error occurs. In the bottom section you'll get an idea which other linux source directories you have to edit.

[Here]("http://www.howtoforge.com/debian_sarge_xen_3.0.3_p2") is a nice tutorial how to build dedicated Xen0 and XenU kernels

Thanks, this saved me wasting a whole lot (more) time! :)

---

### Post by tuxologe on 2007-04-11
> **alben said:**
> 
```

#vi Config.mk                          # near line 36
#vi pristine-linux-2.6.16.29/Makefile  # near line 342
#vi ref-linux-2.6.16.29/Makefile       # this should be hardlinked to the files above
#vi linux-2.6.16.29-xen/Makefile       # this should be hardlinked to the files above

```


Add. for xen 3.0.4:
I tried this very helpful hint in combination with xen-3.0.4_1 and found out that there is at least one additional Makefile which has to be patched:

```

linux-2.6-xen-sparse/arch/<your architecture>/Makefile
<your architecture>=i386|ia64|um|x86_64

```

---

### Post by misse- on 2007-07-18
Hi, I've pasted the line mentioned in the posts above into those 5 different files, and I got past the first couple of errors. However, the compilation still crashes at:

```
make[4]: Entering directory `/home/administrator/xen/xen-3.0.3_0-src/tools/firmware/vmxassist'
cpp -P -DDEBUG -DTEXTADDR=0x000D0000 vmxassist.ld > vmxassist.tmp
ld -o vmxassist -m elf_i386 -nostdlib --fatal-warnings -N -T vmxassist.tmp head.o trap.o vm86.o setup.o util.o
util.o: In function `_doprint':
util.c:(.text+0x363): undefined reference to `__stack_chk_fail'
make[4]: *** [vmxassist.bin] Error 1

```

Any Ideas?

---

