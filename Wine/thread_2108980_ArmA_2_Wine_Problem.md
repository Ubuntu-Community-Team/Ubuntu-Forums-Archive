---
title: "ArmA 2 Wine Problem"
date: 2013-01-26
forum: Wine
---

### Post by linuxsyst on 2013-01-26
That happens when I try to start it with play on linux it just doesn't start... and I arleady copied the X3DAudio1_6.dll file

```
Unhandled exception: assertion failed in 32-bit code (0xf77fa430).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:f77fa430 ESP:0143e894 EBP:7d665200 EFLAGS:00200296(   - --  I S -A-P- )
 EAX:00000000 EBX:000012fa ECX:000012fa EDX:00000006
 ESI:00000000 EDI:f7658ff4
Stack dump:
0x0143e894:  7d665200 00000006 000012fa f74e11df
0x0143e8a4:  f7658ff4 0143e9d0 f74e4825 00000006
0x0143e8b4:  0143e950 00000000 f7658ff4 0000004c
0x0143e8c4:  0000004d 0000004c f751cebc 7d7cb640
0x0143e8d4:  0000004d 0143ea04 7d7cb640 00000000
0x0143e8e4:  00000007 f7658ff4 f74dc0b0 f765a0e0
Backtrace:
=>0 0xf77fa430 __kernel_vsyscall+0x10() in [vdso].so (0x7d665200)
  1 0xf74e11df gsignal+0x4e() in libc.so.6 (0x7d665200)
  2 0xf74e4825 abort+0x174() in libc.so.6 (0x7d665200)
  3 0xf74da085 in libc.so.6 (+0x27084) (0x7d665200)
  4 0xf74da137 __assert_fail+0x56() in libc.so.6 (0x7d665200)
  5 0xf6f030ec nvfx_framebuffer_validate+0x87b() in nouveau_dri.so (0x7d665200)
  6 0xf6f0114a in nouveau_dri.so (+0x64149) (0x00000000)
  7 0xf6f021ed nvfx_state_validate+0x5c() in nouveau_dri.so (0x00000000)
  8 0xf6ee0e77 nvfx_draw_vbo+0xd6() in nouveau_dri.so (0x00000000)
  9 0xf68703ca st_draw_vbo+0x7c9() in libgallium.so (0x7d71fc08)
  10 0xf6d37030 vbo_exec_vtx_flush+0x63f() in libdricore.so (0x7d71f7e8)
  11 0xf6d2c427 in libdricore.so (+0x109426) (0x00000001)
  12 0xf6d3483f vbo_exec_FlushVertices+0x2e() in libdricore.so (0x00000001)
  13 0xf6c80551 _mesa_set_enable+0x1a70() in libdricore.so (0x00000001)
  14 0xf6c807c8 _mesa_Enable+0x57() in libdricore.so (0x0143f2a8)
  15 0x7ecd1fa9 in wined3d (+0xd1fa8) (0x0143f2a8)
  16 0x7ecd3587 in wined3d (+0xd3586) (0x0143f378)
  17 0x7ec4c668 in wined3d (+0x4c667) (0x0143f808)
  18 0x7ec504b0 in wined3d (+0x504af) (0x0143f838)
  19 0x7ecdb0f0 wined3d_create+0x6f() in wined3d (0x0143f888)
  20 0x7dfbf412 in d3d9 (+0x1f411) (0x0143f8b8)
  21 0x7dfb2e7d Direct3DCreate9Ex+0x7c() in d3d9 (0x0143f8f8)
0xf77fa430 __kernel_vsyscall+0x10 in [vdso].so: popl    %ebp
Modules:
Module  Address         Debug info  Name (115 modules)
PE    230000-  237000   Deferred        x3daudio1_6
PE    400000-  c31000   Export          arma2free
ELF 7b800000-7ba33000   Deferred        kernel32<elf>
  \-PE  7b810000-7ba33000   \               kernel32
ELF 7bc00000-7bcca000   Deferred        ntdll<elf>
  \-PE  7bc10000-7bcca000   \               ntdll
ELF 7bf00000-7bf04000   Deferred        <wine-loader>
ELF 7da3c000-7da70000   Deferred        uxtheme<elf>
  \-PE  7da40000-7da70000   \               uxtheme
ELF 7da70000-7da76000   Deferred        libxfixes.so.3
ELF 7da76000-7da81000   Deferred        libxcursor.so.1
ELF 7da81000-7da91000   Deferred        libxi.so.6
ELF 7da91000-7da95000   Deferred        libxcomposite.so.1
ELF 7da95000-7da9e000   Deferred        libxrandr.so.2
ELF 7da9e000-7daa8000   Deferred        libxrender.so.1
ELF 7daa8000-7daae000   Deferred        libxxf86vm.so.1
ELF 7daae000-7dab2000   Deferred        libxinerama.so.1
ELF 7dab2000-7dab9000   Deferred        libxdmcp.so.6
ELF 7dab9000-7dabd000   Deferred        libxau.so.6
ELF 7dabd000-7dade000   Deferred        libxcb.so.1
ELF 7dade000-7dae4000   Deferred        libuuid.so.1
ELF 7dae4000-7dafe000   Deferred        libice.so.6
ELF 7dafe000-7dc32000   Deferred        libx11.so.6
ELF 7dc32000-7dc44000   Deferred        libxext.so.6
ELF 7dc44000-7dc4d000   Deferred        libsm.so.6
ELF 7dc68000-7dcf3000   Deferred        winex11<elf>
  \-PE  7dc70000-7dcf3000   \               winex11
ELF 7dd46000-7dd70000   Deferred        libexpat.so.1
ELF 7dd70000-7dda4000   Deferred        libfontconfig.so.1
ELF 7dda4000-7ddba000   Deferred        libz.so.1
ELF 7ddba000-7de54000   Deferred        libfreetype.so.6
ELF 7de6f000-7de95000   Deferred        d3dxof<elf>
  \-PE  7de70000-7de95000   \               d3dxof
ELF 7de95000-7df04000   Deferred        d3dcompiler_43<elf>
  \-PE  7dea0000-7df04000   \               d3dcompiler_43
ELF 7df04000-7df84000   Deferred        d3dx9_36<elf>
  \-PE  7df10000-7df84000   \               d3dx9_36
ELF 7df84000-7df9e000   Deferred        d3dx9_41<elf>
  \-PE  7df90000-7df9e000   \               d3dx9_41
ELF 7df9e000-7dfd6000   Dwarf           d3d9<elf>
  \-PE  7dfa0000-7dfd6000   \               d3d9
ELF 7dfd6000-7dffa000   Deferred        iphlpapi<elf>
  \-PE  7dfe0000-7dffa000   \               iphlpapi
ELF 7dffa000-7e02d000   Deferred        ws2_32<elf>
  \-PE  7e000000-7e02d000   \               ws2_32
ELF 7e02d000-7e048000   Deferred        wsock32<elf>
  \-PE  7e030000-7e048000   \               wsock32
ELF 7e048000-7e05d000   Deferred        xinput1_3<elf>
  \-PE  7e050000-7e05d000   \               xinput1_3
ELF 7e05d000-7e0f4000   Deferred        msvcrt<elf>
  \-PE  7e070000-7e0f4000   \               msvcrt
ELF 7e0f4000-7e110000   Deferred        dinput8<elf>
  \-PE  7e100000-7e110000   \               dinput8
ELF 7e110000-7e22b000   Deferred        oleaut32<elf>
  \-PE  7e130000-7e22b000   \               oleaut32
ELF 7e22b000-7e328000   Deferred        comctl32<elf>
  \-PE  7e230000-7e328000   \               comctl32
ELF 7e328000-7e397000   Deferred        shlwapi<elf>
  \-PE  7e340000-7e397000   \               shlwapi
ELF 7e397000-7e5b1000   Deferred        shell32<elf>
  \-PE  7e3a0000-7e5b1000   \               shell32
ELF 7e5b1000-7e5f6000   Deferred        dsound<elf>
  \-PE  7e5c0000-7e5f6000   \               dsound
ELF 7e5f6000-7e61f000   Deferred        msacm32<elf>
  \-PE  7e600000-7e61f000   \               msacm32
ELF 7e61f000-7e697000   Deferred        rpcrt4<elf>
  \-PE  7e630000-7e697000   \               rpcrt4
ELF 7e697000-7e7ac000   Deferred        ole32<elf>
  \-PE  7e6b0000-7e7ac000   \               ole32
ELF 7e7ac000-7e85d000   Deferred        winmm<elf>
  \-PE  7e7b0000-7e85d000   \               winmm
ELF 7e85d000-7e9a4000   Deferred        user32<elf>
  \-PE  7e870000-7e9a4000   \               user32
ELF 7e9a4000-7ea09000   Deferred        advapi32<elf>
  \-PE  7e9b0000-7ea09000   \               advapi32
ELF 7ea09000-7eb14000   Deferred        gdi32<elf>
  \-PE  7ea20000-7eb14000   \               gdi32
ELF 7eb14000-7ebeb000   Deferred        opengl32<elf>
  \-PE  7eb30000-7ebeb000   \               opengl32
ELF 7ebeb000-7ed1c000   Dwarf           wined3d<elf>
  \-PE  7ec00000-7ed1c000   \               wined3d
ELF 7ed1c000-7ed86000   Deferred        ddraw<elf>
  \-PE  7ed20000-7ed86000   \               ddraw
ELF 7ef86000-7ef93000   Deferred        libnss_files.so.2
ELF 7ef93000-7ef9f000   Deferred        libnss_nis.so.2
ELF 7ef9f000-7efb9000   Deferred        libnsl.so.1
ELF 7efb9000-7efe5000   Deferred        libm.so.6
ELF 7efe6000-7f000000   Deferred        version<elf>
  \-PE  7eff0000-7f000000   \               version
ELF f52e6000-f52ed000   Deferred        libffi.so.6
ELF f52ed000-f530b000   Deferred        libgcc_s.so.1
ELF f53f0000-f6747000   Deferred        libllvm-3.0.so.1
ELF f6747000-f6b06000   Dwarf           libgallium.so
ELF f6b06000-f6c23000   Deferred        libglsl.so
ELF f6c23000-f6e9d000   Dwarf           libdricore.so
ELF f6e9d000-f726d000   Dwarf           nouveau_dri.so
ELF f726d000-f72c6000   Deferred        libgl.so.1
ELF f7403000-f740a000   Deferred        libdrm_nouveau.so.1
ELF f740a000-f7413000   Deferred        librt.so.1
ELF f7413000-f7420000   Deferred        libdrm.so.2
ELF f7420000-f7438000   Deferred        libxcb-glx.so.0
ELF f7438000-f744e000   Deferred        libglapi.so.0
ELF f7469000-f748c000   Deferred        imm32<elf>
  \-PE  f7470000-f748c000   \               imm32
ELF f748c000-f74a0000   Deferred        psapi<elf>
  \-PE  f7490000-f74a0000   \               psapi
ELF f74a4000-f74ad000   Deferred        libnss_compat.so.2
ELF f74ae000-f74b3000   Deferred        libdl.so.2
ELF f74b3000-f765d000   Dwarf           libc.so.6
ELF f765e000-f7679000   Deferred        libpthread.so.0
ELF f7684000-f7687000   Deferred        libx11-xcb.so.1
ELF f7687000-f768b000   Deferred        libxdamage.so.1
ELF f7694000-f77d6000   Dwarf           libwine.so.1
ELF f77d8000-f77fa000   Deferred        ld-linux.so.2
ELF f77fa000-f77fb000   Dwarf           [vdso].so
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\Program Files (x86)\Bohemia Interactive\ArmA 2 Free\arma2free.exe
    00000028   -2
    00000027    0
    00000024    0
    00000023    0
    00000022    1
    00000009    0 <==
0000000e services.exe
    00000020    0
    0000001f    0
    00000019    0
    00000018    0
    00000017    0
    00000015    0
    00000010    0
    0000000f    0
00000012 winedevice.exe
    0000001d    0
    0000001a    0
    00000014    0
    00000013    0
0000001b plugplay.exe
    00000021    0
    0000001e    0
    0000001c    0
00000025 explorer.exe
    00000026    0
System information:
    Wine build: wine-1.5.22
    Platform: i386 (WOW64)
    Host system: Linux
    Host version: 3.2.0-35-generic
```

---

### Post by linuxsyst on 2013-01-27
Here are the screenshots...

---

### Post by linuxsyst on 2013-01-27
Anyone? please

---

