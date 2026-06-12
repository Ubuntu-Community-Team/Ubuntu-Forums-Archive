---
title: "WIne segfaults with every program"
date: 2007-12-23
forum: Wine
---

### Post by chicken101 on 2007-12-23
I've been using wine to run dc++ for some time with no problems, but today I tried running soul seek and it gave me a segmentation fault.  Now dc++ no longer works.  I tried completely removing wine and reinstalling but that didn't solve the problem.  Also, when i try to run sudo wincfg it segmentation faults also.

Here's the output:

>  sudo wine '/home/chicken/.wine/drive_c/Program Files/DC++/DCPlusPlus.exe' 
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
wine: Unhandled page fault on read access to 0x000000b8 at address 0x7e355889 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x000000b8 in 32-bit code (0x7e355889).
Register dump:
Modules:
Module  Address                 Debug info      Name (56 modules)
PE        400000-  5d7000       Deferred        dcplusplus
ELF     7b800000-7b929000       Dwarf           kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca0000       Dwarf           ntdll<elf>
  \-PE  7bc10000-7bca0000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e2f5000-7e2ff000       Deferred        libdrm.so.2
ELF     7e2ff000-7e530000       Export          r300_dri.so
ELF     7e530000-7e53b000       Deferred        libgcc_s.so.1
ELF     7e53b000-7e5b7000       Export          libgl.so.1
ELF     7e5b7000-7e5bc000       Deferred        libxdmcp.so.6
ELF     7e5bc000-7e5bf000       Deferred        libxau.so.6
ELF     7e5bf000-7e6b0000       Deferred        libx11.so.6
ELF     7e6b0000-7e6be000       Deferred        libxext.so.6
ELF     7e6be000-7e6c3000       Deferred        libxxf86vm.so.1
ELF     7e6c3000-7e6db000       Deferred        libice.so.6
ELF     7e6db000-7e6e3000       Deferred        libsm.so.6
ELF     7e6f9000-7e784000       Dwarf           winex11<elf>
  \-PE  7e710000-7e784000       \               winex11
ELF     7e7fe000-7e81e000       Deferred        libexpat.so.1
ELF     7e81e000-7e849000       Deferred        libfontconfig.so.1
ELF     7e849000-7e85e000       Deferred        libz.so.1
ELF     7e85e000-7e8ce000       Deferred        libfreetype.so.6
ELF     7e8e4000-7e93d000       Deferred        rpcrt4<elf>
  \-PE  7e8f0000-7e93d000       \               rpcrt4
ELF     7e93d000-7e9de000       Deferred        ole32<elf>
  \-PE  7e950000-7e9de000       \               ole32
ELF     7e9de000-7e9f1000       Deferred        libresolv.so.2
ELF     7e9f3000-7ea07000       Deferred        shfolder<elf>
  \-PE  7ea00000-7ea07000       \               shfolder
ELF     7ea07000-7ea25000       Deferred        iphlpapi<elf>
  \-PE  7ea10000-7ea25000       \               iphlpapi
ELF     7ea25000-7ea52000       Deferred        ws2_32<elf>
  \-PE  7ea30000-7ea52000       \               ws2_32
ELF     7ea52000-7eb10000       Deferred        comctl32<elf>
  \-PE  7ea60000-7eb10000       \               comctl32
ELF     7eb10000-7eb69000       Deferred        shlwapi<elf>
  \-PE  7eb20000-7eb69000       \               shlwapi
ELF     7eb69000-7ec6c000       Deferred        shell32<elf>
  \-PE  7eb80000-7ec6c000       \               shell32
ELF     7ec6c000-7ed07000       Dwarf           gdi32<elf>
  \-PE  7ec80000-7ed07000       \               gdi32
ELF     7ed07000-7ee45000       Dwarf           user32<elf>
  \-PE  7ed20000-7ee45000       \               user32
ELF     7ee45000-7ee8e000       Deferred        advapi32<elf>
  \-PE  7ee50000-7ee8e000       \               advapi32
ELF     7efad000-7efc5000       Deferred        libnsl.so.1
ELF     7efc5000-7efea000       Deferred        libm.so.6
ELF     7efeb000-7eff6000       Deferred        libnss_files.so.2
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7cd3000-b7cdc000       Deferred        libnss_compat.so.2
ELF     b7cdd000-b7ce1000       Deferred        libdl.so.2
ELF     b7ce1000-b7e2b000       Deferred        libc.so.6
ELF     b7e2c000-b7e44000       Deferred        libpthread.so.0
ELF     b7e5a000-b7f6e000       Dwarf           libwine.so.1
ELF     b7f70000-b7f8c000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files\DC++\DCPlusPlus.exe
        00000009    0 <==


---

### Post by cogadh on 2007-12-23
NEVER USE SUDO OR A ROOT ACCOUNT TO RUN WINE!!!

From the WineHQ FAQ:
> Should I run Wine as root?

NEVER run Wine as root. Doing so gives Windows programs (and viruses) full access to your computer and every piece of media attached to it. Running with sudo also has these same risks but with the added bonus of breaking the permission on the users ~/.wine folder in the process. If you have run Wine with sudo you need to sudo rm -rf ~/.wine and then run winecfg to set wine back up. You should run Wine as the normal user you use to login.

That's the first thing you need to do. If that doesn't correct your issue, then we'll look into other options.

---

### Post by chicken101 on 2007-12-23
chicken@chicken-desktop:~$ winecfg
wine: creating configuration directory '/home/chicken/.wine'...
Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
wine: Unhandled page fault on read access to 0x000000b8 at address 0x7e6ce889 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x000000b8 in 32-bit code (0x7e6ce889).

I usually ran dc++ with using sudo because i couldn't really use it without doing that. That wasn't the problem i still get the same error.

---

### Post by cogadh on 2007-12-24
> **chicken101 said:**
> Xlib:  extension "ATIFGLRXDRI" missing on display ":0.0".
This concerns me a bit. It looks like the ATI driver is not installed correctly. Unfortunately, I'm not too familiar with ATI on Linux (I've always used Nvidia), so I will have to leave this for someone a bit more familiar with it.

It might be worth it to look into the Linux version of DC++. With the native version, at least you won't run the risks involved in using Wine with root permissions:
[http://linuxdcpp.berlios.de/articles.php?um=index](http://linuxdcpp.berlios.de/articles.php?um=index)

---

### Post by berman56 on 2008-01-13
I have exactly the same problem.  Very frustrating.  I've been searching for answer but to no avail at the moment.  I am a moderately experienced linux user.  The problem is with the ATI driver.  I'll get back to you if I find a solution.

---

### Post by berman56 on 2008-01-13
Managed to solve the problem by reinstalling the ATI driver using ENVY:  

[http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu6_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu6_all.deb)

---

