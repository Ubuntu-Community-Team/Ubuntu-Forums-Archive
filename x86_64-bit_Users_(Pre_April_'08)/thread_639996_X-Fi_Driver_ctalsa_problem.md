---
title: "X-Fi Driver ctalsa problem"
date: 2007-12-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by Afisamuleal on 2007-12-13
Hello; I am an intermediate linux user but I would like help with my X-Fi card.

I have read [this]("http://ubuntuforums.org/showthread.php?t=571656") thread over and over again, and page 13 seems to particularly apply to my problems, however, it has not solved them, and nor have I.

Hardware:
X-Fi Xtreme Gamer
AMD Athalon 64
Biostar Nvidia GeForce 6100-M9 (Socket 939 :D )
Seperate Graphics card -- other unrelated stuff

I am using Gutsy (64 bit) and my /bin/sh is mapped to dash; I am using the default kernel and have no experience with compiling kernels (or doing anything to kernels).

I have tried to recompile my kernel, and I have it as a boot option in grub (I've set the default kernel as the primary, and am using that at the moment), however it disabled the restricted modules drivers, and my nvidia driver proceedingly:

I can handle installing the nvidia drivers from nvidia if need be, but for my own reasons, I would like to avoid as much as I can recompiling the kernel. However, questions:

1) What purpose does recompiling the kernel serve? Why does anyone need to do it; whey don't packages use the kernel someone already has?
2) Why doesn't the restricted drivers module, or anything else that doesn't work, not work when the kernel is recompiled? [based on the previous kernel as detailed in [here]("http://ubuntuforums.org/showthread.php?t=571656")?]

A quick narration of what I've done:

--> download/untar drivers/untar source

```
./configure CC=gcc-3.3
make; sudo make install.
```

The last part of my make install output is as follows:

> ...[No Errors or Warnings]...
Install script files...
/etc/init.d/ctsound already exists. Overwrite it...
FATAL: Error inserting ctalsa (/lib/modules/2.6.22-14-generic/kernel/drivers/ssound/ctalsa.ko): Unknown symbol in module, or unknown parameter (see dmesg)

No soundcards are listed under /proc/asound/cards.

dmesg output:

```

[   55.244371] emupia: Unknown symbol InterlockedIncrement
[   55.244427] emupia: Unknown symbol heap_alloc
[   55.244481] emupia: Unknown symbol stack_free_page
[   55.244585] emupia: Unknown symbol stack_alloc
[   55.244705] emupia: Unknown symbol get_ossrv
[   55.244754] emupia: Unknown symbol unload_all_plugins
[   55.244809] emupia: Unknown symbol stack_alloc_page
[   55.244859] emupia: Unknown symbol ioctl_dispatch
[   55.244910] emupia: Unknown symbol heap_free
[   55.245021] emupia: Unknown symbol InterlockedDecrement
[   55.245076] emupia: Unknown symbol stack_free
[   55.250779] ctsfman: Unknown symbol heap_alloc
[   55.250967] ctsfman: Unknown symbol get_ossrv
[   55.251019] ctsfman: Unknown symbol ioctl_dispatch
[   55.251070] ctsfman: Unknown symbol heap_free
[   55.301706] ct20xut: Unknown symbol InterlockedIncrement
[   55.301765] ct20xut: Unknown symbol heap_alloc
[   55.301826] ct20xut: Unknown symbol unregister_plugin
[   55.301900] ct20xut: Unknown symbol heap_free
[   55.301984] ct20xut: Unknown symbol register_plugin
[   55.302037] ct20xut: Unknown symbol InterlockedDecrement
[   55.412444] ctexfifx: Unknown symbol InterlockedDecrement
[   55.412509] ctexfifx: Unknown symbol register_plugin
[   55.412575] ctexfifx: Unknown symbol unregister_plugin
[   55.412666] ctexfifx: Unknown symbol heap_alloc
[   55.412735] ctexfifx: Unknown symbol InterlockedIncrement
[   55.412787] ctexfifx: Unknown symbol heap_free
[   55.428036] cthwiut: Unknown symbol InterlockedIncrement
[   55.428093] cthwiut: Unknown symbol heap_alloc
[   55.428151] cthwiut: Unknown symbol unregister_plugin
[   55.428225] cthwiut: Unknown symbol heap_free
[   55.428298] cthwiut: Unknown symbol register_plugin
[   55.428345] cthwiut: Unknown symbol InterlockedDecrement
[   55.622399] haxfi: Unknown symbol InterlockedDecrement
[   55.622625] haxfi: Unknown symbol get_ossrv
[   55.622900] haxfi: Unknown symbol heap_alloc
[   55.623042] haxfi: Unknown symbol InterlockedIncrement
[   55.623144] haxfi: Unknown symbol heap_free
[   55.639291] ctalsa: Unknown symbol bytes_to_order
[   55.639788] ctalsa: Unknown symbol get_ossrv
[   55.640832] ctalsa: Unknown symbol heap_alloc
[   55.640970] ctalsa: Unknown symbol malloc_sizes
[   55.641143] ctalsa: Unknown symbol ioctl_dispatch
[   55.641246] ctalsa: Unknown symbol heap_free
[   56.596235] lp0: using parport0 (interrupt-driven).
...
[ 2128.244931] emupia: no version for "InterlockedIncrement" found: kernel tainted.
[ 2134.655004] ctalsa: Unknown symbol malloc_sizes
[ 2183.938882] ctalsa: Unknown symbol malloc_sizes
[ 2217.039373] ctalsa: Unknown symbol malloc_sizes
[ 3031.804389] ctalsa: Unknown symbol malloc_sizes
```

I tried adding

```
-fno-stack-protector
``` to my Makefile.conf file to read as such:
```
CFLAGS                  = -Wall -fomit-frame-pointer **-fno-stack-protector** -Os -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN \
                          -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY -DKBUILD_MODNAME=\"x-fi\" $(INCLUDES)
ifeq ($(USRDLL), y)
CFLAGS                  += -fPIC -D_USRDLL
else
CFLAGS                  += -D__KERNEL__ -DMODULE
endif


ifeq ($(ARCH), x86_64)
    ifneq ($(USRDLL), y)
        CFLAGS          += -mcmodel=kernel
    endif
    CFLAGS              += -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks
    CFLAGS              += -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64
    CFLAGS              += -D__CT_BOUND_64BIT
else
    CFLAGS              += -march=pentium -m32 -D__CT_BOUND_32BIT
endif

CPPFLAGS                = $(INCLUDE) -fno-exceptions -fno-rtti

```

but honestly I didn't check to see what that did or if there was another occurrence or replacement of it already there.

If I need to recompile the kernel, would someone help me through that, and explain what recompiling it does?

Please help me =(

(also, what is the purpose of **-exec touch -c {} \;** in ```
sudo chmod -R 755 XFiDrv_Linux_US-1.04 && find XFiDrv_Linux_US-1.04/ -exec touch -c {} \;
```?)

---

