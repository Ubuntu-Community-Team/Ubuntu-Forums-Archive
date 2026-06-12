---
title: "Wine/Playonlinux is not running Final Fantasy VIII"
date: 2012-11-26
forum: Wine
---

### Post by Shuudoushi on 2012-11-26
I have not been able to find anything about this on the forums, so I **think** it's a new problem.

Specs
OS: Ubuntu 12.04 (64-bit)
Video card: [AMD] nee ATI RS780L [Radeon HD 3000]
Video drivers: Latest ATI/AMD from web-site
Wine ver: 1.5.18
Playonlinux ver: 4.1.8

I have setup playonlinux/wine to run as 64-bit win7. Other than FF8 on the drive i also have FF7 on the virt drive.

The output I'm getting from playonlinux debug is (I know it's very long but never know what's important.):


```
[11/26/12 09:37:53] - Running wine-1.5.18 FF8.exe (Working directory : /home/ichi/.PlayOnLinux/wineprefix/FF/drive_c/Program Files (x86)/Eidos Interactive/Square Soft, Inc/FINAL FANTASY VIII)
err:wgl:has_opengl Failed to load libGL: libGL.so.1: wrong ELF class: ELFCLASS64
err:wgl:has_opengl OpenGL support is disabled.
err:ddraw:ddraw_create_swapchain Failed to create swapchain, hr 0x8876086c.
err:ddraw:ddraw7_SetCooperativeLevel Failed to create swapchain, hr 0x8876086c.
err:wgl:has_opengl Failed to load libGL: libGL.so.1: wrong ELF class: ELFCLASS64
err:wgl:has_opengl OpenGL support is disabled.
wine: Unhandled page fault on read access to 0x00000030 at address 0x7e71e09e (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000030 in 32-bit code (0x7e71e09e).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:7e71e09e ESP:00323b54 EBP:00323bdc EFLAGS:00010246(  R- --  I  Z- -P- )
 EAX:0013b080 EBX:7e7e7f20 ECX:00000000 EDX:00000000
 ESI:00323c58 EDI:00138650
Stack dump:
0x00323b54:  00138674 00323b90 00323bc0 7bc35a9f
0x00323b64:  7e7e7f20 00000003 ffbf05f0 7bca6ef0
0x00323b74:  0013b080 00000000 00138674 00000000
0x00323b84:  00000002 00323bfc 00000000 7bca6ef0
0x00323b94:  7bc71ad9 7bca6ef0 00323d5c 7bc86d3f
0x00323ba4:  7bcafe80 00323bfc 7e84feec 7e7202eb
Backtrace:
=>0 0x7e71e09e wined3d_get_device_caps+0x4be() in wined3d (0x00323bdc)
  1 0x7e70a69d wined3d_device_get_device_caps+0x7c() in wined3d (0x00323c1c)
  2 0x7e8071e3 in ddraw (+0x171e2) (0x00323f7c)
  3 0x0040c6a7 in ff8 (+0xc6a6) (0x00324dac)
  4 0x0043abf2 in ff8 (+0x3abf1) (0x00324df0)
  5 0x00409574 in ff8 (+0x9573) (0x00324e1c)
  6 0x0040190a in ff8 (+0x1909) (0x00324fd0)
  7 0x00569913 in ff8 (+0x169912) (0x0032fde4)
  8 0x0055ace7 in ff8 (+0x15ace6) (0x0032fe70)
  9 0x7b85d27c call_process_entry+0xb() in kernel32 (0x0032fe88)
  10 0x7b8608ab in kernel32 (+0x508aa) (0x0032fec8)
  11 0x7bc72d00 call_thread_func_wrapper+0xb() in ntdll (0x0032fed8)
  12 0x7bc72f5d call_thread_func+0x7c() in ntdll (0x0032ffa8)
  13 0x7bc72cde RtlRaiseException+0x21() in ntdll (0x0032ffc8)
  14 0x7bc4c59e in ntdll (+0x3c59d) (0x0032ffe8)
0x7e71e09e wined3d_get_device_caps+0x4be in wined3d: call    *0x30(%ecx)
Modules:
Module    Address            Debug info    Name (71 modules)
PE      330000-  366000    Deferred        binkw32
PE      400000- 27a0000    Export          ff8
PE    10000000-1000a000    Deferred        eax
ELF    7b800000-7ba2d000    Dwarf           kernel32<elf>
  \-PE    7b810000-7ba2d000    \               kernel32
ELF    7bc00000-7bcc3000    Dwarf           ntdll<elf>
  \-PE    7bc10000-7bcc3000    \               ntdll
ELF    7bf00000-7bf03000    Deferred        <wine-loader>
ELF    7e137000-7e158000    Deferred        imm32<elf>
  \-PE    7e140000-7e158000    \               imm32
ELF    7e158000-7e18b000    Deferred        uxtheme<elf>
  \-PE    7e160000-7e18b000    \               uxtheme
ELF    7e18b000-7e191000    Deferred        libxfixes.so.3
ELF    7e191000-7e19c000    Deferred        libxcursor.so.1
ELF    7e19c000-7e1ac000    Deferred        libxi.so.6
ELF    7e1ac000-7e1b0000    Deferred        libxcomposite.so.1
ELF    7e1b0000-7e1b9000    Deferred        libxrandr.so.2
ELF    7e1b9000-7e1c3000    Deferred        libxrender.so.1
ELF    7e1c3000-7e1c9000    Deferred        libxxf86vm.so.1
ELF    7e1c9000-7e1cd000    Deferred        libxinerama.so.1
ELF    7e1cd000-7e1d4000    Deferred        libxdmcp.so.6
ELF    7e1d4000-7e1d8000    Deferred        libxau.so.6
ELF    7e1d8000-7e1f9000    Deferred        libxcb.so.1
ELF    7e1f9000-7e1ff000    Deferred        libuuid.so.1
ELF    7e1ff000-7e333000    Deferred        libx11.so.6
ELF    7e333000-7e345000    Deferred        libxext.so.6
ELF    7e345000-7e35f000    Deferred        libice.so.6
ELF    7e35f000-7e368000    Deferred        libsm.so.6
ELF    7e368000-7e3f1000    Deferred        winex11<elf>
  \-PE    7e370000-7e3f1000    \               winex11
ELF    7e3f1000-7e407000    Deferred        libz.so.1
ELF    7e407000-7e4a1000    Deferred        libfreetype.so.6
ELF    7e4b9000-7e5ac000    Deferred        comctl32<elf>
  \-PE    7e4c0000-7e5ac000    \               comctl32
ELF    7e5ac000-7e5f0000    Deferred        dinput<elf>
  \-PE    7e5b0000-7e5f0000    \               dinput
ELF    7e5f0000-7e6bc000    Deferred        opengl32<elf>
  \-PE    7e610000-7e6bc000    \               opengl32
ELF    7e6bc000-7e7ec000    Dwarf           wined3d<elf>
  \-PE    7e6d0000-7e7ec000    \               wined3d
ELF    7e7ec000-7e850000    Dwarf           ddraw<elf>
  \-PE    7e7f0000-7e850000    \               ddraw
ELF    7e850000-7e878000    Deferred        msacm32<elf>
  \-PE    7e860000-7e878000    \               msacm32
ELF    7e878000-7e926000    Deferred        winmm<elf>
  \-PE    7e880000-7e926000    \               winmm
ELF    7e926000-7e96a000    Deferred        dsound<elf>
  \-PE    7e930000-7e96a000    \               dsound
ELF    7e96a000-7e9e0000    Deferred        rpcrt4<elf>
  \-PE    7e980000-7e9e0000    \               rpcrt4
ELF    7e9e0000-7eae6000    Deferred        ole32<elf>
  \-PE    7ea00000-7eae6000    \               ole32
ELF    7eae6000-7ebe8000    Deferred        gdi32<elf>
  \-PE    7eaf0000-7ebe8000    \               gdi32
ELF    7ebe8000-7ed28000    Deferred        user32<elf>
  \-PE    7ec00000-7ed28000    \               user32
ELF    7ed28000-7ed89000    Deferred        advapi32<elf>
  \-PE    7ed30000-7ed89000    \               advapi32
ELF    7ef89000-7ef96000    Deferred        libnss_files.so.2
ELF    7ef96000-7efa2000    Deferred        libnss_nis.so.2
ELF    7efa2000-7efbc000    Deferred        libnsl.so.1
ELF    7efbc000-7efe8000    Deferred        libm.so.6
ELF    7efe8000-7f000000    Deferred        version<elf>
  \-PE    7eff0000-7f000000    \               version
ELF    f73e3000-f73ec000    Deferred        libnss_compat.so.2
ELF    f73ed000-f73f2000    Deferred        libdl.so.2
ELF    f73f2000-f759c000    Deferred        libc.so.6
ELF    f759c000-f75b7000    Deferred        libpthread.so.0
ELF    f75d0000-f7711000    Dwarf           libwine.so.1
ELF    f7713000-f7735000    Deferred        ld-linux.so.2
ELF    f7735000-f7736000    Deferred        [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files (x86)\Eidos Interactive\Square Soft, Inc\FINAL FANTASY VIII\FF8.exe
    00000009    0 <==
0000000e services.exe
    0000001f    0
    0000001e    0
    00000018    0
    00000017    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001c    0
    00000019    0
    00000014    0
    00000013    0
0000001a plugplay.exe
    00000020    0
    0000001d    0
    0000001b    0
00000023 explorer.exe
    00000024    0
```[LEFT]
The bulk of this debug info is what pops up **after **I click *close/cancel* ok the crash dialog box.
Anytime i try to launch the game the error "Unable to locate DirectDraw-compatible graphics card. Final Fantasy VIII requires a DirectDraw-compliant graphics card.". I was only able to get that far by using Wine ver 1.5.18. Other than the debug output and that error message it's the same old crash windows that everyone has seen and read 1000 times. Any help at all would be great! Thanks in advance.
[/LEFT]

---

### Post by Shuudoushi on 2012-11-26
Okay... So the above problem is fixedish... I think.... But now PlayonLinux says it can't find my 32bit opengl libs **OR** my 64bit opengl libs.... I am so lost atm on trying to fix it..... Help please...

---

### Post by Shuudoushi on 2012-11-27
Latest output from PlayonLinux dedug:

```
[11/27/12 12:19:43] - Running wine-1.5.18 FF8.exe (Working directory : /home/ichi/.PlayOnLinux/wineprefix/FF/drive_c/Program Files (x86)/Eidos Interactive/Square Soft, Inc/FINAL FANTASY VIII)
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  139 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  172
  Current serial number in output stream:  172
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  139 (ATIFGLEXTENSION)
  Minor opcode of failed request:  66 ()
  Serial number of failed request:  225
  Current serial number in output stream:  225
```

I will be getting a new ATI/AMD video card in the next few days and thus new drivers. If the problem continues I will update this post... Again...

---

### Post by Shuudoushi on 2012-11-28
I'm still unsure what caused the problem; but after jacking up unity with compizconfig; reinstalling Ubuntu fixed the problem. Now I just have to figure out why the game is not picking up my keyboard commands... Which I am rather sure is not a problem with Ubuntu but the game it's self. Marked as [SOLVED]!

---

