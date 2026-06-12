---
title: "tony hawk 3 doesn't start"
date: 2008-05-31
forum: Wine
---

### Post by pavolzetor on 2008-05-31
hello, my friend install game tony hawk 3 (manual [http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=3823](http://appdb.winehq.org/objectManager.php?bShowAll=true&bIsQueue=false&bIsRejected=false&sClass=version&sTitle=&sReturnTo=&iId=3823))

but he has problems
```
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:winedevice:ServiceMain driver L"pjsapdg" failed to load
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
miso@miso-laptop:~$ err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Setting 32-bit
Setting resolution 3 (1280x1024)
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x7f22f21c,0x00000000), stub!
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
wine: Unhandled page fault on read access to 0x00000006 at address 0x43454b (thread 0023), starting debugger...
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
Unhandled exception: page fault on read access to 0x00000006 in 32-bit code (0x0043454b).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:0043454b ESP:7f22fbcc EBP:78334df8 EFLAGS:00210206(   - 00      - RIP1)
 EAX:00000000 EBX:00000000 ECX:c4614a00 EDX:005b6a42
 ESI:78334df8 EDI:00000000
Stack dump:
0x7f22fbcc:  ffffffff 78334df8 0058d690 00000000
0x7f22fbdc:  78334df8 0043451d 34861a16 78334df8
0x7f22fbec:  00433c76 78334d00 78334df8 7f22fc1c
0x7f22fbfc:  0057d486 00000001 00437ef3 0058d5ac
0x7f22fc0c:  00000002 7f021088 78334d00 00000002
0x7f22fc1c:  7f22fd30 0057dbaf 00000003 0043680c
Backtrace:
=>1 0x0043454b in skate3 (+0x3454b) (0x78334df8)
  2 0x00000000 (0x0058db0c)
  3 0x00594ea4 in skate3 (+0x194ea4) (0x00433c90)
  4 0x00000028 (0xe8f18b56)
0x0043454b: cmpw   %bx,0x6(%edi)
Modules:
Module   Address         Debug info   Name (127 modules)
PE     400000-  975000   Export          skate3
PE   10000000-100f0000   Deferred        platform
PE   21100000-2115e000   Deferred        mss32
PE   22100000-22114000   Deferred        mssa3d.m3d
PE   22200000-22216000   Deferred        mssa3d2.m3d
PE   22300000-22311000   Deferred        mssds3ds.m3d
PE   22400000-22414000   Deferred        mssds3dh.m3d
PE   22500000-22514000   Deferred        msseax.m3d
PE   22600000-22616000   Deferred        mssfast.m3d
PE   22700000-22717000   Deferred        mssdolby.m3d
PE   22900000-22912000   Deferred        mssdx7sl.m3d
PE   22a00000-22a12000   Deferred        mssdx7sh.m3d
PE   22b00000-22b13000   Deferred        mssdx7sn.m3d
PE   22c00000-22c18000   Deferred        msseax2.m3d
PE   22d00000-22d64000   Deferred        mssrsx.m3d
PE   24100000-2410d000   Deferred        lowpass.flt
PE   24200000-2420d000   Deferred        highpass.flt
PE   24300000-2430d000   Deferred        bandpass.flt
PE   24400000-2440d000   Deferred        reverb1.flt
PE   24500000-24510000   Deferred        reverb2.flt
PE   24600000-24611000   Deferred        reverb3.flt
PE   24700000-2470d000   Deferred        reson.flt
PE   24800000-24810000   Deferred        phaser.flt
PE   24900000-2490d000   Deferred        parmeq.flt
PE   24a00000-24a0d000   Deferred        mdelay.flt
PE   24b00000-24b0d000   Deferred        sdelay.flt
PE   24c00000-24c0d000   Deferred        ringmod.flt
PE   24d00000-24d0d000   Deferred        flange.flt
PE   24e00000-24e0d000   Deferred        chorus.flt
PE   24f00000-24f10000   Deferred        shelfeq.flt
PE   25100000-2510d000   Deferred        compress.flt
PE   25200000-2520d000   Deferred        autopan.flt
PE   25300000-2530e000   Deferred        laginter.flt
PE   25400000-2540b000   Deferred        capture.flt
PE   26400000-2642c000   Deferred        mssv29.asi
PE   26500000-26525000   Deferred        mssv24.asi
PE   26600000-26627000   Deferred        mssv12.asi
PE   26f00000-26f2a000   Deferred        mp3dec.asi
ELF   7b800000-7b92c000   Deferred        kernel32<elf>
  \-PE   7b820000-7b92c000   \               kernel32
ELF   7bc00000-7bca5000   Deferred        ntdll<elf>
  \-PE   7bc10000-7bca5000   \               ntdll
ELF   7bf00000-7bf03000   Deferred        <wine-loader>
ELF   7c2c6000-7c310000   Deferred        dsound<elf>
  \-PE   7c2d0000-7c310000   \               dsound
ELF   7d673000-7e188000   Deferred        libglcore.so.1
ELF   7e188000-7e22c000   Deferred        libgl.so.1
ELF   7e22c000-7e24b000   Deferred        imm32<elf>
  \-PE   7e230000-7e24b000   \               imm32
ELF   7e24b000-7e25f000   Deferred        midimap<elf>
  \-PE   7e250000-7e25f000   \               midimap
ELF   7e25f000-7e285000   Deferred        msacm32<elf>
  \-PE   7e270000-7e285000   \               msacm32
ELF   7e285000-7e29c000   Deferred        msacm32<elf>
  \-PE   7e290000-7e29c000   \               msacm32
ELF   7e29c000-7e35f000   Deferred        libasound.so.2
ELF   7e372000-7e3a8000   Deferred        winealsa<elf>
  \-PE   7e380000-7e3a8000   \               winealsa
ELF   7e3d7000-7e3d9000   Deferred        libnvidia-tls.so.1
ELF   7e3ee000-7e420000   Deferred        uxtheme<elf>
  \-PE   7e3f0000-7e420000   \               uxtheme
ELF   7e420000-7e429000   Deferred        libxcursor.so.1
ELF   7e429000-7e42e000   Deferred        libxfixes.so.3
ELF   7e42e000-7e431000   Deferred        libxcomposite.so.1
ELF   7e431000-7e437000   Deferred        libxrandr.so.2
ELF   7e437000-7e43f000   Deferred        libxrender.so.1
ELF   7e43f000-7e442000   Deferred        libxinerama.so.1
ELF   7e442000-7e447000   Deferred        libxdmcp.so.6
ELF   7e447000-7e45f000   Deferred        libxcb.so.1
ELF   7e45f000-7e461000   Deferred        libxcb-xlib.so.0
ELF   7e461000-7e464000   Deferred        libxau.so.6
ELF   7e464000-7e54b000   Deferred        libx11.so.6
ELF   7e54b000-7e559000   Deferred        libxext.so.6
ELF   7e559000-7e55e000   Deferred        libxxf86vm.so.1
ELF   7e571000-7e602000   Deferred        winex11<elf>
  \-PE   7e580000-7e602000   \               winex11
ELF   7e626000-7e647000   Deferred        libexpat.so.1
ELF   7e647000-7e671000   Deferred        libfontconfig.so.1
ELF   7e671000-7e686000   Deferred        libz.so.1
ELF   7e686000-7e6f6000   Deferred        libfreetype.so.6
ELF   7e6f6000-7e75f000   Deferred        msvcrt<elf>
  \-PE   7e710000-7e75f000   \               msvcrt
ELF   7e75f000-7e773000   Deferred        lz32<elf>
  \-PE   7e760000-7e773000   \               lz32
ELF   7e773000-7e78c000   Deferred        version<elf>
  \-PE   7e780000-7e78c000   \               version
ELF   7e78c000-7e88d000   Deferred        wined3d<elf>
  \-PE   7e7a0000-7e88d000   \               wined3d
ELF   7e88d000-7e8b8000   Deferred        d3d8<elf>
  \-PE   7e890000-7e8b8000   \               d3d8
ELF   7e8b8000-7e946000   Deferred        winmm<elf>
  \-PE   7e8c0000-7e946000   \               winmm
ELF   7e946000-7e97d000   Deferred        dinput<elf>
  \-PE   7e950000-7e97d000   \               dinput
ELF   7e97d000-7e995000   Deferred        dinput8<elf>
  \-PE   7e980000-7e995000   \               dinput8
ELF   7e995000-7e9c1000   Deferred        ws2_32<elf>
  \-PE   7e9a0000-7e9c1000   \               ws2_32
ELF   7e9c1000-7e9d4000   Deferred        libresolv.so.2
ELF   7e9d4000-7e9f2000   Deferred        iphlpapi<elf>
  \-PE   7e9e0000-7e9f2000   \               iphlpapi
ELF   7e9f2000-7ea52000   Deferred        rpcrt4<elf>
  \-PE   7ea00000-7ea52000   \               rpcrt4
ELF   7ea52000-7eaf6000   Deferred        ole32<elf>
  \-PE   7ea60000-7eaf6000   \               ole32
ELF   7eaf6000-7ebb5000   Deferred        comctl32<elf>
  \-PE   7eb00000-7ebb5000   \               comctl32
ELF   7ebb5000-7ec0e000   Deferred        shlwapi<elf>
  \-PE   7ebc0000-7ec0e000   \               shlwapi
ELF   7ec0e000-7ed18000   Deferred        shell32<elf>
  \-PE   7ec20000-7ed18000   \               shell32
ELF   7ed18000-7ed69000   Deferred        advapi32<elf>
  \-PE   7ed20000-7ed69000   \               advapi32
ELF   7ed69000-7ee04000   Deferred        gdi32<elf>
  \-PE   7ed80000-7ee04000   \               gdi32
ELF   7ee04000-7ef4a000   Deferred        user32<elf>
  \-PE   7ee20000-7ef4a000   \               user32
ELF   7ef4a000-7ef55000   Deferred        libnss_files.so.2
ELF   7ef55000-7ef6d000   Deferred        libnsl.so.1
ELF   7efc8000-7efed000   Deferred        libm.so.6
ELF   f7ce1000-f7ceb000   Deferred        libnss_nis.so.2
ELF   f7cec000-f7cf0000   Deferred        libdl.so.2
ELF   f7cf0000-f7e3f000   Deferred        libc.so.6
ELF   f7e40000-f7e58000   Deferred        libpthread.so.0
ELF   f7e58000-f7e61000   Deferred        libnss_compat.so.2
ELF   f7e6b000-f7f80000   Deferred        libwine.so.1
ELF   f7f82000-f7fa1000   Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c
   00000017    0
   00000016    0
   00000013    0
   00000010    0
   0000000e    0
   0000000d    0
00000011
   00000015    0
   00000014    0
   00000012    0
0000001d
   0000001f    0
   0000001e    0
00000022 (D) C:\Program Files\Activision\Thps3\Skate3.exe
   00000026   15
   00000025   15
   00000024    0
   00000023    0 <==
Backtrace:
=>1 0x0043454b in skate3 (+0x3454b) (0x78334df8)
  2 0x00000000 (0x0058db0c)
  3 0x00594ea4 in skate3 (+0x194ea4) (0x00433c90)
  4 0x00000028 (0xe8f18b56) 
```

---

### Post by cogadh on 2008-06-01
You can get rid of those preloader errors by following the instructions here:
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)
After correcting that, some of the additional errors may go away. However, just prior to the start of the page fault that actually caused the crash, the game encountered an unrecognized vertex shader problem, which could either mean the game is trying to do something that Wine can't (unlikely, since the game worked on two year old versions of Wine), or your hardware is not capable of using vertex shaders, or it could just be a syptom of the preloader problem. After applying the preloader fix, re-run the game and lets see what errors still remain.

---

