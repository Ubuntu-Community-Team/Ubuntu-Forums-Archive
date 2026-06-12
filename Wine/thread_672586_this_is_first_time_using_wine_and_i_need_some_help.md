---
title: "this is first time using wine and i need some help"
date: 2008-01-19
forum: Wine
---

### Post by 900donuts on 2008-01-19
i'm trying to install battlefield 1942 on my computer using wine this is my first time using wine for anything also space on my computer is cramped so i need to make sure it installs on my second harddrive which has more free space

i already installed the recent version wine of wine what do i do next?

thanks in advance

---

### Post by happyhamster on 2008-01-19
- Concerning the first part, I know of a way, but it's a pain to work with IMO. (If someone knows of a better way, please share.)

By default, wine creates the mock windows filesytem in your home dir (in a hidden folder ".wine"). If you want it somewhere else, you can do it like this:

wineprefixcreate --prefix /path-to-where-ever/.wine

(You can also choose another folder name than .wine.)

- Next, each time you want to run something wine-related, you have to point to it. For example, if you want to run winecfg (to configure wine) you'll have to run:

env WINEPREFIX="/path-to-where-ever/.wine" winecfg

- If you want to run an installer:

env WINEPREFIX="/path-to-where-ever/.wine" wine /media/cdrom0/Autorun.exe
 (or setup.exe or such, and assuming your cdrom drive is mounted at /media/cdrom0.)

- Concerning Battlefield 1942: it should run fine with wine 0.9.53 or 0.9.52. Just run the install-executable as in the example above. And if something goes wrong, your friendly terminal will tell you :) For more info, go here:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7591](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7591)

[edit: for more info on wine, visit: [http://gaming.gwos.org/doku.php/wine:winestuff]](http://gaming.gwos.org/doku.php/wine:winestuff])

---

### Post by 900donuts on 2008-01-19
terminal out put 

wine: Unhandled page fault on read access to 0x99c00000 at address 0x7bc46450 (thread 0009), starting debugger...
First chance exception: page fault on read access to 0x99c00000 in 32-bit code (0x7bc46450).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc46450 ESP:0034fd90 EBP:0034feb8 EFLAGS:00010286(   - 00      -RISP1)
 EAX:00000000 EBX:7bc85434 ECX:ffffffff EDX:00400000
 ESI:004096cc EDI:99c00000
Stack dump:
0x0034fd90:  00110000 00000002 00000020 0034fe28
0x0034fda0:  00000000 00000000 00000000 00000000
0x0034fdb0:  004096cc 7bc7cb90 7bc8d630 7bc7cb90
0x0034fdc0:  0034fe14 0034fe18 00000000 00000000
0x0034fdd0:  00000000 00000000 00000000 99c00000
0x0034fde0:  00000000 18000004 7bc602ba 7bc85434
Backtrace:
=>1 0x7bc46450 in ntdll (+0x36450) (0x0034feb8)
  2 0x7bc47e1b LdrInitializeThunk+0xf6() in ntdll (0x0034ff08)
  3 0x7b86eb0a in kernel32 (+0x4eb0a) (0x0034ffe8)
  4 0xb7e7a1cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7bc46450: repne scasb %es:(%edi)
Modules:
Module  Address                 Debug info      Name (16 modules)
PE        400000-  42c000       Deferred        setup
ELF     7b800000-7b925000       Export          kernel32<elf>
  \-PE  7b820000-7b925000       \               kernel32
ELF     7bc00000-7bca1000       Export          ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7ef91000-7ef9c000       Deferred        libnss_files.so.2
ELF     7ef9c000-7efa6000       Deferred        libnss_nis.so.2
ELF     7efa6000-7efbe000       Deferred        libnsl.so.1
ELF     7efbe000-7efc7000       Deferred        libnss_compat.so.2
ELF     7efc7000-7efec000       Deferred        libm.so.6
ELF     b7cf9000-b7cfd000       Deferred        libdl.so.2
ELF     b7cfd000-b7e47000       Deferred        libc.so.6
ELF     b7e47000-b7e5f000       Deferred        libpthread.so.0
ELF     b7e73000-b7f87000       Export          libwine.so.1
ELF     b7f89000-b7fa5000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
        0000000f    0
        0000000e    0
        0000000d    0
0000000a 
        0000000b    0
00000008 (D) D:\setup.exe
        00000009    0 <==
Backtrace:
=>1 0x7bc46450 in ntdll (+0x36450) (0x0034feb8)
  2 0x7bc47e1b LdrInitializeThunk+0xf6() in ntdll (0x0034ff08)
  3 0x7b86eb0a in kernel32 (+0x4eb0a) (0x0034ffe8)
  4 0xb7e7a1cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)

EDIT: DARN SMILES HOW DO I TURN THOSE OFF

---

### Post by happyhamster on 2008-01-19
Which wine version are you using? And which Ubuntu flavor; regular or the 64 bits?

---

### Post by happyhamster on 2008-01-19
Just noticed that the 0.9.53 entry in the application database is confusing: it says it installs ok, but only when using 0.9.52.

So,  in case you're using the latest wine: getting rid of 0.9.53 and installing 0.9.52 is your best bet I guess. You can download a .deb file here: 

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

After downloading, get rid of the current wine:

sudo apt-get remove --purge wine

Then install 0.9.52 by double-clicking the .deb file. Good luck.

---

### Post by 900donuts on 2008-01-19
down graded to 0.9.52 heres the output from the terminal

```
wine: Unhandled page fault on read access to 0x99c00000 at address 0x7bc46428 (thread 0009), starting debugger...
First chance exception: page fault on read access to 0x99c00000 in 32-bit code (0x7bc46428).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7bc46428 ESP:0034fd90 EBP:0034feb8 EFLAGS:00010286(   - 00      -RISP1)
 EAX:00000000 EBX:7bc858d4 ECX:ffffffff EDX:00400000
 ESI:004096cc EDI:99c00000
Stack dump:
0x0034fd90:  00110000 00000002 00000020 0034fe28
0x0034fda0:  00000000 00000000 00000000 00000000
0x0034fdb0:  004096cc 7bc7c510 7bc8da90 7bc7c510
0x0034fdc0:  0034fe14 0034fe18 00000000 00000000
0x0034fdd0:  00000000 00000000 00000000 99c00000
0x0034fde0:  00000000 18000004 7bc60206 7bc858d4
Backtrace:
=>1 0x7bc46428 in ntdll (+0x36428) (0x0034feb8)
  2 0x7bc47df3 LdrInitializeThunk+0xf6() in ntdll (0x0034ff08)
  3 0x7b86eafa in kernel32 (+0x4eafa) (0x0034ffe8)
  4 0xb7e361cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x7bc46428: repne scasb %es:(%edi)
Modules:
Module  Address                 Debug info      Name (16 modules)
PE        400000-  42c000       Deferred        setup
ELF     7b800000-7b925000       Export          kernel32<elf>
  \-PE  7b820000-7b925000       \               kernel32
ELF     7bc00000-7bca1000       Export          ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7efa4000-7efaf000       Deferred        libnss_files.so.2
ELF     7efaf000-7efc7000       Deferred        libnsl.so.1
ELF     7efc7000-7efec000       Deferred        libm.so.6
ELF     7efed000-7eff7000       Deferred        libnss_nis.so.2
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7cb5000-b7cb9000       Deferred        libdl.so.2
ELF     b7cb9000-b7e03000       Deferred        libc.so.6
ELF     b7e03000-b7e1b000       Deferred        libpthread.so.0
ELF     b7e2f000-b7f43000       Export          libwine.so.1
ELF     b7f45000-b7f61000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) D:\setup.exe
        00000009    0 <==
Backtrace:
=>1 0x7bc46428 in ntdll (+0x36428) (0x0034feb8)
  2 0x7bc47df3 LdrInitializeThunk+0xf6() in ntdll (0x0034ff08)
  3 0x7b86eafa in kernel32 (+0x4eafa) (0x0034ffe8)
  4 0xb7e361cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000) 
```

---

