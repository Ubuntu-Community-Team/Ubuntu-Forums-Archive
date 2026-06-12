---
title: "[wine] Unhandled exception: page fault on write access"
date: 2015-06-17
forum: Wine
---

### Post by jbmarin on 2015-06-17
Hello,

I've installed playonlinux and CAESAR III. I've played some game without trouble but since I've launch the single user mode, I succed the first three missions and I cannot play the 4th because CAESAR freez (when I lauch mission, a cinematic should be played...)

Here the stack trace :

```
Unhandled exception: page fault on write access to 0x0049682c in 32-bit code (0x0045da0a).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0045da0a ESP:0032fd1c EBP:0032fd34 EFLAGS:00210a87(  R- --O I S - -P-C)
 EAX:00000258 EBX:7b8b5000 ECX:ffee5f00 EDX:00000000
 ESI:7ffdf000 EDI:0052d2a0
Stack dump:
0x0032fd1c:  7ffdf000 00000036 00000cb6 00000001
0x0032fd2c:  00000258 00000000 0032fd3c 004cfcb6
0x0032fd3c:  0032fd54 004d00bd 0000012b 00000003
0x0032fd4c:  00000004 00068516 0032fd68 00526c1d
0x0032fd5c:  00000000 00000004 00000006 0032fd80
0x0032fd6c:  00500d5c 005bae40 0000029f 000001ee
000c: sel=0067 base=00000000 limit=00000000 32-bit r-x
Backtrace:
=>0 0x0045da0a in c3 (+0x5da0a) (0x0032fd34)
  1 0x004cfcb6 in c3 (+0xcfcb5) (0x0032fd3c)
  2 0x004d00bd in c3 (+0xd00bc) (0x0032fd54)
  3 0x00526c1d in c3 (+0x126c1c) (0x0032fd68)
  4 0x00500d5c in c3 (+0x100d5b) (0x0032fd80)
  5 0x004d071b in c3 (+0xd071a) (0x0032fd8c)
  6 0x004d030d in c3 (+0xd030c) (0x0032fda0)
  7 0x00418332 in c3 (+0x18331) (0x0032fda8)
  8 0x00418280 in c3 (+0x1827f) (0x0032fdd0)
  9 0x0052d46c in c3 (+0x12d46b) (0x0032fe60)
  10 0x7b85e5cc call_process_entry+0xb() in kernel32 (0x0032fe78)
  11 0x7b85f653 in kernel32 (+0x4f652) (0x0032feb8)
  12 0x7bc799b0 call_thread_func_wrapper+0xb() in ntdll (0x0032fed8)
  13 0x7bc7c93d call_thread_func+0x7c() in ntdll (0x0032ffa8)
  14 0x7bc7998e RtlRaiseException+0x21() in ntdll (0x0032ffc8)
  15 0x7bc4e8fe call_dll_entry_point+0x7ed() in ntdll (0x0032ffe8)
  16 0xf753d50d wine_call_on_stack+0x1c() in libwine.so.1 (0x00000000)
  17 0xf753d5cb wine_switch_to_stack+0x2a() in libwine.so.1 (0xffaf7a88)
  18 0x7bc541e2 LdrInitializeThunk+0x3a1() in ntdll (0xffaf7ae8)
  19 0x7b865bdd __wine_kernel_init+0xa0c() in kernel32 (0xffaf8c08)
  20 0x7bc547a3 __wine_process_init+0x192() in ntdll (0xffaf8c98)
  21 0xf753ac70 wine_init+0x30f() in libwine.so.1 (0xffaf8cf8)
  22 0x7bf00fdc main+0xfb() in <wine-loader> (0xffaf9148)
  23 0xf7356a83 __libc_start_main+0xf2() in libc.so.6 (0x00000000)
0x0045da0a: movl    $0x0,0x5b092c(%ecx,%edx,8)
Modules:
Module    Address            Debug info    Name (136 modules)
PE      400000-  963000    Export          c3
PE    10000000-1001b000    Deferred        smackw32
ELF    7b800000-7ba5b000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba5b000    \               kernel32
ELF    7ba88000-7bc00000    Deferred        libvorbisenc.so.2
ELF    7bc00000-7bcdb000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcdb000    \               ntdll
ELF    7bf00000-7bf04000    Dwarf           <wine-loader>
ELF    7bf36000-7bf62000    Deferred        libvorbis.so.0
ELF    7bf62000-7bfd4000    Deferred        libsndfile.so.1
ELF    7bfd4000-7c0ca000    Deferred        libasound.so.2
ELF    7c0ca000-7c200000    Deferred        oleaut32<elf>
  \-PE    7c0e0000-7c200000    \               oleaut32
ELF    7c40d000-7c47c000    Deferred        libpulsecommon-4.0.so
ELF    7c47c000-7c4cb000    Deferred        libpulse.so.0
ELF    7c8c5000-7c8f9000    Deferred        libflac.so.8
ELF    7c90b000-7c912000    Deferred        libasound_module_pcm_pulse.so
ELF    7c920000-7c950000    Deferred        winealsa<elf>
  \-PE    7c930000-7c950000    \               winealsa
ELF    7cb50000-7cb87000    Deferred        libtxc_dxtn.so
ELF    7cb87000-7cb90000    Deferred        libogg.so.0
ELF    7cb90000-7cb97000    Deferred        libasyncns.so.0
ELF    7cb97000-7cba2000    Deferred        libjson-c.so.2
ELF    7cba2000-7cbc4000    Deferred        mmdevapi<elf>
  \-PE    7cbb0000-7cbc4000    \               mmdevapi
ELF    7cbcf000-7cbda000    Deferred        libpciaccess.so.0
ELF    7cbda000-7cbf7000    Deferred        libgcc_s.so.1
ELF    7ccdf000-7cced000    Deferred        libdrm_radeon.so.1
ELF    7cced000-7ccf5000    Deferred        libdrm_nouveau.so.2
ELF    7ccf5000-7cd18000    Deferred        libdrm_intel.so.1
ELF    7cd18000-7d28b000    Deferred        i965_dri.so
ELF    7d28b000-7d295000    Deferred        libnih-dbus.so.1
ELF    7d295000-7d2ae000    Deferred        libnih.so.1
ELF    7d2ae000-7d2cc000    Deferred        libcgmanager.so.0
ELF    7d2cc000-7d2df000    Deferred        libudev.so.1
ELF    7d2df000-7d2ed000    Deferred        libdrm.so.2
ELF    7d2ed000-7d2f4000    Deferred        libxcb-sync.so.1
ELF    7d2f4000-7d2f8000    Deferred        libxcb-present.so.0
ELF    7d2f8000-7d310000    Deferred        libxcb-glx.so.0
ELF    7d310000-7d328000    Deferred        libglapi.so.0
ELF    7d328000-7d388000    Deferred        libgl.so.1
ELF    7d3af000-7d3b9000    Deferred        libwrap.so.0
ELF    7d6af000-7d6d4000    Deferred        imm32<elf>
  \-PE    7d6c0000-7d6d4000    \               imm32
ELF    7d71a000-7d74a000    Deferred        p11-kit-trust.so
ELF    7d74a000-7d753000    Deferred        librt.so.1
ELF    7d753000-7d75a000    Deferred        libffi.so.6
ELF    7d75a000-7d75f000    Deferred        libgpg-error.so.0
ELF    7d75f000-7d777000    Deferred        libresolv.so.2
ELF    7d777000-7d77b000    Deferred        libkeyutils.so.1
ELF    7d77b000-7d7c6000    Deferred        libdbus-1.so.3
ELF    7d7c6000-7d802000    Deferred        libp11-kit.so.0
ELF    7d802000-7d816000    Deferred        libtasn1.so.6
ELF    7d816000-7d89c000    Deferred        libgcrypt.so.11
ELF    7d89c000-7d8a8000    Deferred        libkrb5support.so.0
ELF    7d8a8000-7d8d8000    Deferred        libk5crypto.so.3
ELF    7d8d8000-7d996000    Deferred        libkrb5.so.3
ELF    7d996000-7da5c000    Deferred        libgnutls.so.26
ELF    7da5c000-7daa1000    Deferred        libgssapi_krb5.so.2
ELF    7daa1000-7db0e000    Deferred        libcups.so.2
ELF    7db0e000-7db11000    Deferred        libxshmfence.so.1
ELF    7db11000-7db15000    Deferred        libxcb-dri3.so.0
ELF    7db15000-7db1b000    Deferred        libxcb-dri2.so.0
ELF    7db1b000-7db1e000    Deferred        libx11-xcb.so.1
ELF    7db1e000-7db22000    Deferred        libxdamage.so.1
ELF    7db22000-7db35000    Deferred        gnome-keyring-pkcs11.so
ELF    7db35000-7db6c000    Deferred        uxtheme<elf>
  \-PE    7db40000-7db6c000    \               uxtheme
ELF    7db6c000-7db72000    Deferred        libxfixes.so.3
ELF    7db72000-7db7d000    Deferred        libxcursor.so.1
ELF    7db7d000-7db8d000    Deferred        libxi.so.6
ELF    7db8d000-7db91000    Deferred        libxcomposite.so.1
ELF    7db91000-7db9c000    Deferred        libxrandr.so.2
ELF    7db9c000-7dba7000    Deferred        libxrender.so.1
ELF    7dba7000-7dbad000    Deferred        libxxf86vm.so.1
ELF    7dbad000-7dbb1000    Deferred        libxinerama.so.1
ELF    7dbb1000-7dbb8000    Deferred        libxdmcp.so.6
ELF    7dbb8000-7dbbc000    Deferred        libxau.so.6
ELF    7dbbc000-7dbde000    Deferred        libxcb.so.1
ELF    7dbde000-7dd12000    Deferred        libx11.so.6
ELF    7dd12000-7dd25000    Deferred        libxext.so.6
ELF    7dd25000-7dd2a000    Deferred        libcom_err.so.2
ELF    7dd2a000-7dd3c000    Deferred        libavahi-client.so.3
ELF    7dd3c000-7dd4a000    Deferred        libavahi-common.so.3
ELF    7dd4c000-7ddde000    Deferred        winex11<elf>
  \-PE    7dd60000-7ddde000    \               winex11
ELF    7de57000-7de80000    Deferred        libexpat.so.1
ELF    7de80000-7debb000    Deferred        libfontconfig.so.1
ELF    7debb000-7dee3000    Deferred        libpng12.so.0
ELF    7dee3000-7defd000    Deferred        libz.so.1
ELF    7defd000-7df9d000    Deferred        libfreetype.so.6
ELF    7dfea000-7e015000    Deferred        msacm32<elf>
  \-PE    7dff0000-7e015000    \               msacm32
ELF    7e015000-7e0cf000    Deferred        winmm<elf>
  \-PE    7e020000-7e0cf000    \               winmm
ELF    7e0cf000-7e118000    Deferred        dsound<elf>
  \-PE    7e0e0000-7e118000    \               dsound
ELF    7e118000-7e227000    Deferred        opengl32<elf>
  \-PE    7e130000-7e227000    \               opengl32
ELF    7e227000-7e367000    Deferred        wined3d<elf>
  \-PE    7e230000-7e367000    \               wined3d
ELF    7e367000-7e3dc000    Deferred        ddraw<elf>
  \-PE    7e370000-7e3dc000    \               ddraw
ELF    7e3dc000-7e45d000    Deferred        rpcrt4<elf>
  \-PE    7e3f0000-7e45d000    \               rpcrt4
ELF    7e45d000-7e599000    Deferred        ole32<elf>
  \-PE    7e470000-7e599000    \               ole32
ELF    7e599000-7e5d9000    Deferred        winspool<elf>
  \-PE    7e5a0000-7e5d9000    \               winspool
ELF    7e5d9000-7e6e0000    Deferred        comctl32<elf>
  \-PE    7e5e0000-7e6e0000    \               comctl32
ELF    7e6e0000-7e75a000    Deferred        shlwapi<elf>
  \-PE    7e6f0000-7e75a000    \               shlwapi
ELF    7e75a000-7e98d000    Deferred        shell32<elf>
  \-PE    7e770000-7e98d000    \               shell32
ELF    7e98d000-7ea78000    Deferred        comdlg32<elf>
  \-PE    7e990000-7ea78000    \               comdlg32
ELF    7ea78000-7eaea000    Deferred        advapi32<elf>
  \-PE    7ea80000-7eaea000    \               advapi32
ELF    7eaea000-7ec07000    Deferred        gdi32<elf>
  \-PE    7eb00000-7ec07000    \               gdi32
ELF    7ec07000-7ed61000    Deferred        user32<elf>
  \-PE    7ec20000-7ed61000    \               user32
ELF    7ef61000-7ef6e000    Deferred        libnss_files.so.2
ELF    7ef6e000-7ef7a000    Deferred        libnss_nis.so.2
ELF    7ef7a000-7ef93000    Deferred        libnsl.so.1
ELF    7ef93000-7efd9000    Deferred        libm.so.6
ELF    7efe6000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    f7333000-f733c000    Deferred        libnss_compat.so.2
ELF    f733d000-f74eb000    Dwarf           libc.so.6
ELF    f74eb000-f74f0000    Deferred        libdl.so.2
ELF    f74f1000-f750d000    Deferred        libpthread.so.0
ELF    f7534000-f76e9000    Dwarf           libwine.so.1
ELF    f76eb000-f770d000    Deferred        ld-linux.so.2
ELF    f770d000-f770e000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\SIERRA\Caesar3\c3.exe
    00000035   15
    0000002a   15
    00000029    0
    00000024    0
    00000009    0 <==
0000000e services.exe
    0000001e    0
    0000001d    0
    00000014    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001c    0
    00000019    0
    00000017    0
    00000013    0
0000001a plugplay.exe
    00000020    0
    0000001f    0
    0000001b    0
00000021 explorer.exe
    00000023    0
    00000022    0
System information:
    Wine build: wine-1.6.2
    Platform: i386
    Host system: Linux
    Host version: 3.13.0-55-generic

```

---

### Post by Bucky Ball on 2015-06-17
*Thread moved to **Wine**.*

---

