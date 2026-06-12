---
title: "Starcraft in Wine?"
date: 2012-10-10
forum: Wine
---

### Post by Anton45665 on 2012-10-10
can someone fix this bug / glitch .. i am new here dont know how to post new thread 

Unhandled exception: page fault on read access to 0x0000001c in 32-bit code (0x7da9e39b).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7da9e39b ESP:0033f5cc EBP:0033f604 EFLAGS:00010286(  R- --  I S - -P- )
 EAX:ffffffff EBX:7daedff4 ECX:00139b80 EDX:00000003
 ESI:0033f73c EDI:00000000
Stack dump:
0x0033f5cc:  00000003 7daf1874 7dada081 7dad9d87
0x0033f5dc:  00000000 0033f73c 7eadb7a3 0000000a
0x0033f5ec:  00000005 7bcc2568 7daa6dcb 7dba7ff4
0x0033f5fc:  0033f7dc 80070057 0033f7a4 7db5caec
0x0033f60c:  00000000 0033f73c 0033f778 00000464
0x0033f61c:  0013b190 0033f660 7eaceef8 00000464
000c: sel=0067 base=00000000 limit=00000000 16-bit --x
Backtrace:
=>0 0x7da9e39b wined3d_swapchain_get_desc+0x5b() in wined3d (0x0033f604)
  1 0x7db5caec in ddraw (+0xcaeb) (0x0033f7a4)
  2 0x7db5d7d1 in ddraw (+0xd7d0) (0x0033f874)
  3 0x0041db09 in starcraft (+0x1db08) (0x0033fd04)
  4 0x004db0a7 in starcraft (+0xdb0a6) (0x0033fd24)
  5 0x004e0847 in starcraft (+0xe0846) (0x0033fd3c)
  6 0x004e0b20 in starcraft (+0xe0b1f) (0x0033fd48)
  7 0x00404da5 in starcraft (+0x4da4) (0x0033fe70)
  8 0x7b859cdc call_process_entry+0xb() in kernel32 (0x0033fe88)
  9 0x7b85af4f in kernel32 (+0x4af4e) (0x0033fec8)
  10 0x7bc71db0 call_thread_func_wrapper+0xb() in ntdll (0x0033fed8)
  11 0x7bc7486d call_thread_func+0x7c() in ntdll (0x0033ffa8)
  12 0x7bc71d8e RtlRaiseException+0x21() in ntdll (0x0033ffc8)
  13 0x7bc49f4e call_dll_entry_point+0x61d() in ntdll (0x0033ffe8)
0x7da9e39b wined3d_swapchain_get_desc+0x5b in wined3d: movl    0x1c(%edi),%eax
Modules:
Module    Address            Debug info    Name (88 modules)
PE      400000-  6ec000    Export          starcraft
PE     2000000- 2011000    Deferred        local
PE    15000000-15069000    Deferred        storm
ELF    7b800000-7ba15000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba15000    \               kernel32
ELF    7bc00000-7bcc3000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcc3000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7d9bf000-7daf3000    Dwarf           wined3d<elf>
  \-PE    7d9d0000-7daf3000    \               wined3d
ELF    7db43000-7dbab000    Dwarf           ddraw<elf>
  \-PE    7db50000-7dbab000    \               ddraw
ELF    7dbab000-7dbb4000    Deferred        librt.so.1
ELF    7dbb4000-7dbb9000    Deferred        libgpg-error.so.0
ELF    7dbb9000-7dbd1000    Deferred        libresolv.so.2
ELF    7dbd1000-7dbd5000    Deferred        libkeyutils.so.1
ELF    7dbd5000-7dc1e000    Deferred        libdbus-1.so.3
ELF    7dc1e000-7dc30000    Deferred        libp11-kit.so.0
ELF    7dc30000-7dcb5000    Deferred        libgcrypt.so.11
ELF    7dcb5000-7dcc7000    Deferred        libtasn1.so.3
ELF    7dcc7000-7dcd0000    Deferred        libkrb5support.so.0
ELF    7dcd0000-7dcf8000    Deferred        libk5crypto.so.3
ELF    7dcf8000-7ddc7000    Deferred        libkrb5.so.3
ELF    7ddc7000-7ddd9000    Deferred        libavahi-client.so.3
ELF    7ddd9000-7de9d000    Deferred        libgnutls.so.26
ELF    7de9d000-7dedb000    Deferred        libgssapi_krb5.so.2
ELF    7dedb000-7df2e000    Deferred        libcups.so.2
ELF    7df44000-7dfb9000    Deferred        rpcrt4<elf>
  \-PE    7df50000-7dfb9000    \               rpcrt4
ELF    7dfb9000-7e0c1000    Deferred        ole32<elf>
  \-PE    7dfd0000-7e0c1000    \               ole32
ELF    7e0ef000-7e123000    Deferred        uxtheme<elf>
  \-PE    7e100000-7e123000    \               uxtheme
ELF    7e123000-7e129000    Deferred        libxfixes.so.3
ELF    7e129000-7e134000    Deferred        libxcursor.so.1
ELF    7e135000-7e13a000    Deferred        libcom_err.so.2
ELF    7e13a000-7e148000    Deferred        libavahi-common.so.3
ELF    7e1a9000-7e1d3000    Deferred        libexpat.so.1
ELF    7e1d3000-7e207000    Deferred        libfontconfig.so.1
ELF    7e207000-7e217000    Deferred        libxi.so.6
ELF    7e217000-7e21b000    Deferred        libxcomposite.so.1
ELF    7e21b000-7e224000    Deferred        libxrandr.so.2
ELF    7e224000-7e22e000    Deferred        libxrender.so.1
ELF    7e22e000-7e234000    Deferred        libxxf86vm.so.1
ELF    7e234000-7e238000    Deferred        libxinerama.so.1
ELF    7e238000-7e23f000    Deferred        libxdmcp.so.6
ELF    7e23f000-7e243000    Deferred        libxau.so.6
ELF    7e243000-7e264000    Deferred        libxcb.so.1
ELF    7e264000-7e26a000    Deferred        libuuid.so.1
ELF    7e26a000-7e284000    Deferred        libice.so.6
ELF    7e284000-7e3b8000    Deferred        libx11.so.6
ELF    7e3b8000-7e3ca000    Deferred        libxext.so.6
ELF    7e3ca000-7e45d000    Deferred        winex11<elf>
  \-PE    7e3d0000-7e45d000    \               winex11
ELF    7e45d000-7e473000    Deferred        libz.so.1
ELF    7e473000-7e50d000    Deferred        libfreetype.so.6
ELF    7e50d000-7e547000    Deferred        winspool<elf>
  \-PE    7e510000-7e547000    \               winspool
ELF    7e547000-7e626000    Deferred        comdlg32<elf>
  \-PE    7e550000-7e626000    \               comdlg32
ELF    7e648000-7e740000    Deferred        comctl32<elf>
  \-PE    7e650000-7e740000    \               comctl32
ELF    7e740000-7e7aa000    Deferred        shlwapi<elf>
  \-PE    7e750000-7e7aa000    \               shlwapi
ELF    7e7aa000-7e9bb000    Deferred        shell32<elf>
  \-PE    7e7c0000-7e9bb000    \               shell32
ELF    7e9bb000-7e9dd000    Deferred        imm32<elf>
  \-PE    7e9c0000-7e9dd000    \               imm32
ELF    7e9dd000-7e9f6000    Deferred        version<elf>
  \-PE    7e9e0000-7e9f6000    \               version
ELF    7e9f6000-7ea56000    Deferred        advapi32<elf>
  \-PE    7ea00000-7ea56000    \               advapi32
ELF    7ea56000-7eb13000    Deferred        gdi32<elf>
  \-PE    7ea60000-7eb13000    \               gdi32
ELF    7eb13000-7ec53000    Deferred        user32<elf>
  \-PE    7eb20000-7ec53000    \               user32
ELF    7ec53000-7ec6d000    Deferred        libnsl.so.1
ELF    7ec6d000-7ec76000    Deferred        libnss_compat.so.2
ELF    7efbe000-7efea000    Deferred        libm.so.6
ELF    7efea000-7eff3000    Deferred        libsm.so.6
ELF    7eff3000-7f000000    Deferred        libnss_files.so.2
ELF    f74a1000-f74a6000    Deferred        libdl.so.2
ELF    f74a6000-f764b000    Deferred        libc.so.6
ELF    f764c000-f7667000    Deferred        libpthread.so.0
ELF    f7671000-f767d000    Deferred        libnss_nis.so.2
ELF    f767d000-f77bf000    Dwarf           libwine.so.1
ELF    f77c1000-f77e3000    Deferred        ld-linux.so.2
ELF    f77e3000-f77e4000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001f    0
    0000001e    0
    0000001c    0
    00000017    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001b    0
    00000018    0
    00000014    0
    00000013    0
00000019 plugplay.exe
    00000020    0
    0000001d    0
    0000001a    0
00000021 explorer.exe
    00000022    0
00000023 (D) Z:\home\anton\Skrivbord\StarCraft.exe
    00000025    1
    00000024    0 <==
System information:
    Wine build: wine-1.4
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.2.0-31-generic

---

