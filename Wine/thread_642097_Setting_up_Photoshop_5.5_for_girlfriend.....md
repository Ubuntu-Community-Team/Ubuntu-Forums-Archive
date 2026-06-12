---
title: "Setting up Photoshop 5.5 for girlfriend...."
date: 2007-12-16
forum: Wine
---

### Post by Kharun on 2007-12-16
1. Wine version - Latest version...0.9.51
   2. Terminal output - [email]root@*****-desktop:/home/*****/.wine[/email]/drive_c/Program Files/Setup# wine setup.exe

wine: Unhandled page fault on read access to 0x80400000 at address 0xb7d4f583 (thread 000e), starting debugger...

Unhandled exception: page fault on read access to 0x80400000 in 32-bit code (0xb7d4f583).

Register dump:

 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b

 EIP:b7d4f583 ESP:0034fd9c EBP:0034fea8 EFLAGS:00010246(   - 00      -RIZP1)

 EAX:80400000 EBX:7bc8443c ECX:00000000 EDX:0047ea28

 ESI:00110770 EDI:00110770

Stack dump:

0x0034fd9c:  7bc45cd3 80400000 00000000 000001f4

0x0034fdac:  0034fe90 00000000 00000000 00000000

0x0034fdbc:  00000000 00000000 00000000 00000000

0x0034fdcc:  00000000 0034fe90 00000000 00000000

0x0034fddc:  00000000 00110480 001106b0 00110770

0x0034fdec:  00000000 0000007d 00000000 00000000

Backtrace:

=>1 0xb7d4f583 strlen+0x33() in libc.so.6 (0x0034fea8)

  2 0x7bc46620 LdrInitializeThunk+0x110(unknown1=0x0, unknown2=0x0, unknown3=0x0, unknown4=0x0) [/build/buildd/wine-0.9.46/dlls/ntdll/loader.c:2313] in ntdll (0x0034ff08)

  3 0x7b874c4a start_process+0xba(arg=0x0) [/build/buildd/wine-0.9.46/dlls/kernel32/process.c:829] in kernel32 (0x0034ffe8)

  4 0xb7e579d7 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

0xb7d4f583 strlen+0x33 in libc.so.6: movl       0x0(%eax),%ecx

Modules:

Module  Address                 Debug info      Name (16 modules)

PE        400000-  48d000       Deferred        _ins5576._mp

ELF     7b800000-7b929000       Dwarf           kernel32<elf>

  \-PE  7b820000-7b929000       \               kernel32

ELF     7bc00000-7bca0000       Dwarf           ntdll<elf>

  \-PE  7bc10000-7bca0000       \               ntdll

ELF     7bf00000-7bf03000       Deferred        <wine-loader>

ELF     7ee74000-7ee7f000       Deferred        libnss_files.so.2

ELF     7ee7f000-7ee97000       Deferred        libnsl.so.1

ELF     7ee97000-7eea0000       Deferred        libnss_compat.so.2

ELF     7efcd000-7eff2000       Deferred        libm.so.6

ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2

ELF     b7cdb000-b7cdf000       Deferred        libdl.so.2

ELF     b7cdf000-b7e29000       Export          libc.so.6

ELF     b7e2a000-b7e42000       Deferred        libpthread.so.0

ELF     b7e50000-b7f64000       Dwarf           libwine.so.1

ELF     b7f66000-b7f82000       Deferred        ld-linux.so.2

Threads:

process  tid      prio (all id:s are in hex)

0000000d (D) C:\windows\temp\_ISTMP3.DIR\_INS5576._MP

        0000000e    0 <==

0000000a 

        0000000c    0

        0000000b    0

00000008 

        00000009    0

3. Wine configuration - How you have Wine configured changes how Wine behaves greatly and may be the cause of whatever issue you may be having. Configuration items to consider including are :

* OS version: Windows XP
* Library overrides: None
* Sound settings, all options: Whatever the defaults are
* Graphics settings, all options: 
Allow DirectX apps to stop the mouse leaving their window. 
Allow the window manager to control the windows.
Emualte a virtual deskop.
Vertex Shader Support: Hardware.
Allow Pixel Shader: Checked
* Registry edits: None

4. Hardware specs/drivers - 

Intel P4 3.0GHz (Socket 478)
1 GB DDR400 RAM
Nvidia Geforce FX 5700LE 256MB (with restricted drivers enabled)
20GB ATA HD
DVD-RW Burner
Netgear Wireless card
and various other hardware pieces that don't matter

5. Other Wine applications - Nothing yet...everything else my girlfriend wants is in here in one form or another :P


I made sure to copy the terminal output for those who might need it. I haven't been using Linux for too long, so I'm a bit uneasy tinkering with anything on my own, so I decided to come here and hope for the best...

I was over at [http://frankscorner.org/](http://frankscorner.org/) and I followed the directions to install Photoshop 5.5 and the installer loader comes up, flies (really fast) up to 99% and then it appears to hang. After a minute or two, it just disappears and the terminal window goes back to the input line...any clue based on the output what might be going wrong?

Thanks all, and here's to a successful Christmas present/project for the girlfriend!

---

### Post by Sockerdrickan on 2007-12-16
Teach her GIMP, I say! ;)

---

### Post by Kharun on 2007-12-16
Tried that...she's been on photoshop for over 5 years and knows every in and out...and is a bit stubborn I'm afraid about GIMP and it's quote: "Wacky Interface and odd button layout."

---

