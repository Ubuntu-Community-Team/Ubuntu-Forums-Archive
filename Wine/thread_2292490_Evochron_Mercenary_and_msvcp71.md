---
title: "Evochron Mercenary and msvcp71"
date: 2015-08-28
forum: Wine
---

### Post by arieleoar on 2015-08-28
Hi there!

I've got some trouble trying to run evochron mercenary, as in windows i can run perfectly in this pc (is dual boot), in wine produces two kind of errors:

(NOTE: I've basic knowledge of programming, don't get angry if i've made wrong conclussions of the data i got.)

*First with msvcp71 as built-in, the application crashes badly with this output:

```
 [FONT=monospace][COLOR=#000000]wine /media/leo/DATOS/Juegos\ XP/Evochron.Mercenary.v2.848.wth-keygen-THETA/EvochronMercenary.exe  [/COLOR]
err:winediag:wined3d_dll_init The GLSL shader backend has been disabled. You get to keep all the pieces if it breaks. 
fixme:wbemprox:wbem_services_CreateInstanceEnum unsupported flags 0x00000030 
fixme:wbemprox:enum_class_object_Next timeout not supported 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no fallback
 specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no fallback
 specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32G32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32G32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32G32B32A32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no
 fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32G32B32A32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no
 fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no fallback
 specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no fallback
 specified.                                                                                                                                      
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no fallb
ack specified.                                                                                                                                   
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no fallb
ack specified.                                                                                                                                   
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16B16A16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no
 fallback specified.                                                                                                                             
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16B16A16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no
 fallback specified.                                                                                                                             
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fallb
ack specified.                                                                                                                                   
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fallb
ack specified.                                                                                                                                   
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8A8_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fal
lback specified.                                                                                                                                 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8A8_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fal
lback specified.                                                                                                                                 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8X8_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fal
lback specified.                                                                                                                                 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8X8_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fal
lback specified.                                                                                                                                 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B5G6R5_UNORM rtInternal format is not supported as FBO color attachment, type 0.                    
fixme:d3d:check_fbo_compat Format WINED3DFMT_B5G6R5_UNORM rtInternal format is not supported as FBO color attachment, type 2.                    
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fallback 
specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 1), and no fallback 
specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fallback 
specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 3), and no fallback 
specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R10G10B10A2_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no 
fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R10G10B10A2_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no 
fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8G8B8A8_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fal
lback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8G8B8A8_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fal
lback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B10G10R10A2_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no 
fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B10G10R10A2_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no 
fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16B16A16_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no
 fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16B16A16_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no
 fallback specified. 
fixme:win:EnumDisplayDevicesW ((null),0,0xe2d1f8,0x00000000), stub! 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no fallback
 specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no fallback
 specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32G32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32G32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32G32B32A32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no
 fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32G32B32A32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no
 fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no fallback
 specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no fallback
 specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16B16A16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no
 fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16B16A16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no
 fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8A8_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fal
lback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8A8_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fal
lback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8X8_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fal
lback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8X8_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fal
lback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B5G6R5_UNORM rtInternal format is not supported as FBO color attachment, type 0. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B5G6R5_UNORM rtInternal format is not supported as FBO color attachment, type 2. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fallback 
specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 1), and no fallback 
specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fallback 
specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 3), and no fallback 
specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R10G10B10A2_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no 
fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R10G10B10A2_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no 
fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8G8B8A8_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fal
lback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8G8B8A8_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fal
lback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B10G10R10A2_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no 
fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B10G10R10A2_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no 
fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16B16A16_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no
 fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16B16A16_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no
 fallback specified. 
fixme:win:EnumDisplayDevicesW ((null),0,0xe2cfe8,0x00000000), stub! 
fixme:ddraw:ddraw7_Initialize Ignoring guid {aeb2cdd4-6e41-43ea-941c-8361cc760781}. 
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {33d9a761-90c8-11d0-bd43-00a0c911ce86} not found 
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found 
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found 
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0026), starting debugger... 
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000). 
Register dump: 
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b 
 EIP:00000000 ESP:00e2f4d8 EBP:00e2f4dc EFLAGS:00210206(  R- --  I   - -P- ) 
 EAX:100377e0 EBX:00000001 ECX:00000000 EDX:00000000 
 ESI:00e2f4f4 EDI:00e2fdc0 
Stack dump: 
0x00e2f4d8:  10002db2 00e2f4ec 100038e0 cccccccc 
0x00e2f4e8:  cccccccc 00e2f50c 0040a18e 00e2f514 
0x00e2f4f8:  cccccccc cccccccc cccccccc cccccccc 
0x00e2f508:  00421638 00e2fdd0 004027a0 bcf484bd 
0x00e2f518:  fffffffe 00000000 00000001 cccccccc 
0x00e2f528:  00244248 cccccccc cccccccc cccccccc 
Backtrace: 
=>0 0x00000000 (0x00e2f4dc) 
  1 0x100038e0 in dbprocore (+0x38df) (0x00e2f4ec) 
  2 0x0040a18e in evochronmercenary (+0xa18d) (0x00e2f50c) 
  3 0x004027a0 in evochronmercenary (+0x279f) (0x00e2fdd0) 
  4 0x0040be1b in evochronmercenary (+0xbe1a) (0x00e2fe60) 
  5 0x7b8611ec call_process_entry+0xb() in kernel32 (0x00e2fe78) 
  6 0x7b8622c3 in kernel32 (+0x522c2) (0x00e2feb8) 
  7 0x7bc81ab0 call_thread_func_wrapper+0xb() in ntdll (0x00e2fed8) 
  8 0x7bc84c7d call_thread_func+0x7c() in ntdll (0x00e2ffa8) 
  9 0x7bc81a8e RtlRaiseException+0x21() in ntdll (0x00e2ffc8) 
  10 0x7bc5523e call_dll_entry_point+0x3fd() in ntdll (0x00e2ffe8) 
  11 0xb75a865d wine_call_on_stack+0x1c() in libwine.so.1 (0x00000000) 
  12 0xb75a871b wine_switch_to_stack+0x2a() in libwine.so.1 (0xbfff2288) 
  13 0x7bc5adb9 LdrInitializeThunk+0x238() in ntdll (0xbfff22c8) 
  14 0x7b868b33 __wine_kernel_init+0xa12() in kernel32 (0xbfff33e8) 
  15 0x7bc5bce3 __wine_process_init+0x192() in ntdll (0xbfff3478) 
  16 0xb75a5dc8 wine_init+0x327() in libwine.so.1 (0xbfff34d8) 
  17 0x7bf0100c main+0xfb() in <wine-loader> (0xbfff3928) 
  18 0xb73b472e __libc_start_main+0xdd() in libc.so.6 (0x00000000) 
0x00000000: -- no code accessible -- 
Modules: 
Module  Address                 Debug info      Name (190 modules) 
PE        370000-  38d000       Deferred        dbproinputdebug 
PE        390000-  3ae000       Deferred        dbprotextdebug 
PE        3b0000-  3d4000       Deferred        dbprofiledebug 
PE        3e0000-  3f6000       Deferred        dbprobasic2ddebug 
PE        400000-  429000       Export          evochronmercenary 
PE       9600000- 96ae000       Deferred        dinput8 
PE       9af0000- 9bca000       Deferred        mikenet 
PE       9ce0000- 9d08000       Deferred        dbprosystemdebug 
PE       9e20000- 9e9f000       Deferred        enhancements 
PE       9fb0000- 9fd2000       Deferred        dbprosetupdebug 
PE       a200000- a223000       Deferred        dbprocameradebug 
PE       a340000- c2f1000       Deferred        dbprobasic3ddebug 
PE       c410000- c42c000       Deferred        dbprolightdebug 
PE       c540000- c561000       Deferred        dbprovectorsdebug 
PE       c680000- c6a0000       Deferred        dbproimagedebug 
PE       c7b0000- c859000       Deferred        dbprosounddebug 
PE       c970000- c98a000       Deferred        dbprobitmapdebug 
PE       caa0000- caae000       Deferred        input_plugin 
PE       cbd0000- cbf6000       Deferred        dbproanimationdebug 
PE       cd10000- cdc4000       Deferred        eap155 
PE       cee0000- cee6000       Deferred        kd01_anisotropicfiltering 
PE       d000000- d075000       Deferred        sc_collision 
PE       d190000- d1a5000       Deferred        dbpromemblocksdebug 
PE      10000000-10041000       Export          dbprocore 
ELF     7a800000-7a91f000       Deferred        opengl32<elf> 
  \-PE  7a820000-7a91f000       \               opengl32 
ELF     7b800000-7ba65000       Dwarf           kernel32<elf> 
  \-PE  7b810000-7ba65000       \               kernel32 
ELF     7bc00000-7bce8000       Dwarf           ntdll<elf> 
  \-PE  7bc10000-7bce8000       \               ntdll 
ELF     7bf00000-7bf04000       Dwarf           <wine-loader> 
PE      7c140000-7c243000       Deferred        mfc71 
ELF     7e363000-7e388000       Deferred        imm32<elf> 
  \-PE  7e370000-7e388000       \               imm32 
ELF     7e451000-7e47a000       Deferred        libexpat.so.1 
ELF     7e47a000-7e4bd000       Deferred        libfontconfig.so.1 
ELF     7e4bd000-7e4e9000       Deferred        libpng12.so.0 
ELF     7e4e9000-7e504000       Deferred        libz.so.1 
ELF     7e504000-7e5b4000       Deferred        libfreetype.so.6 
ELF     7e5b4000-7e5d7000       Deferred        libtinfo.so.5 
ELF     7e5d7000-7e5ff000       Deferred        libncurses.so.5 
ELF     7e624000-7e769000       Deferred        oleaut32<elf> 
  \-PE  7e640000-7e769000       \               oleaut32 
ELF     7e769000-7e7ed000       Deferred        rpcrt4<elf> 
  \-PE  7e770000-7e7ed000       \               rpcrt4 
ELF     7e7ed000-7e92f000       Deferred        ole32<elf> 
  \-PE  7e800000-7e92f000       \               ole32 
ELF     7e92f000-7e9ab000       Deferred        advapi32<elf> 
  \-PE  7e940000-7e9ab000       \               advapi32 
ELF     7e9ab000-7eaca000       Deferred        gdi32<elf> 
  \-PE  7e9c0000-7eaca000       \               gdi32 
ELF     7eaca000-7ec26000       Deferred        user32<elf> 
  \-PE  7eae0000-7ec26000       \               user32 
ELF     7ef58000-7ef66000       Deferred        libnss_files.so.2 
ELF     7ef66000-7ef73000       Deferred        libnss_nis.so.2 
ELF     7ef73000-7ef8e000       Deferred        libnsl.so.1 
ELF     7ef8e000-7efdb000       Deferred        libm.so.6 
ELF     7efe6000-7f000000       Deferred        version<elf> 
  \-PE  7eff0000-7f000000       \               version 
ELF     af23b000-af255000       Deferred        d3dx9_35<elf> 
  \-PE  af240000-af255000       \               d3dx9_35 
ELF     af255000-af31b000       Deferred        msvcr100<elf> 
  \-PE  af270000-af31b000       \               msvcr100 
ELF     af31b000-af38c000       Deferred        setupapi<elf> 
  \-PE  af330000-af38c000       \               setupapi 
ELF     af38c000-af3a2000       Deferred        hid<elf> 
  \-PE  af390000-af3a2000       \               hid 
ELF     af3a2000-af3b7000       Deferred        xinput1_3<elf> 
  \-PE  af3b0000-af3b7000       \               xinput1_3 
ELF     af3b7000-af42c000       Deferred        d3dcompiler_43<elf> 
  \-PE  af3c0000-af42c000       \               d3dcompiler_43 
ELF     af42c000-af4bb000       Deferred        d3dx9_36<elf> 
  \-PE  af440000-af4bb000       \               d3dx9_36 
ELF     af4bb000-af5a8000       Deferred        comdlg32<elf> 
  \-PE  af4c0000-af5a8000       \               comdlg32 
ELF     af5a8000-af652000       Deferred        msvcr71<elf> 
  \-PE  af5c0000-af652000       \               msvcr71 
ELF     af652000-af89c000       Deferred        shell32<elf> 
  \-PE  af660000-af89c000       \               shell32 
ELF     af89c000-af8b2000       Deferred        midimap<elf> 
  \-PE  af8a0000-af8b2000       \               midimap 
ELF     af8b2000-af9a8000       Deferred        libasound.so.2 
ELF     af9b4000-af9cd000       Deferred        msacm32<elf> 
  \-PE  af9c0000-af9cd000       \               msacm32 
ELF     af9cd000-af9ff000       Deferred        winealsa<elf> 
  \-PE  af9d0000-af9ff000       \               winealsa 
ELF     b3b35000-b3b62000       Deferred        libvorbis.so.0 
ELF     b3b62000-b3b6b000       Deferred        libogg.so.0 
ELF     b3b6b000-b3b7f000       Deferred        libgpg-error.so.0 
ELF     b3b7f000-b3c0e000       Deferred        libvorbisenc.so.2 
ELF     b3c0e000-b3c6f000       Deferred        libflac.so.8 
ELF     b3c6f000-b3d20000       Deferred        libgcrypt.so.20 
ELF     b3d20000-b3d46000       Deferred        liblzma.so.5 
ELF     b3d46000-b3d4f000       Deferred        librt.so.1 
ELF     b3d4f000-b3d56000       Deferred        libasyncns.so.0 
ELF     b3d56000-b3dcf000       Deferred        libsndfile.so.1 
ELF     b3dcf000-b3dd9000       Deferred        libwrap.so.0 
ELF     b3dd9000-b3e06000       Deferred        libsystemd.so.0 
ELF     b3e06000-b3e8b000       Deferred        libpulsecommon-6.0.so 
ELF     b3e8b000-b3e97000       Deferred        libjson-c.so.2 
ELF     b3e97000-b3ef0000       Deferred        libpulse.so.0 
ELF     b3f15000-b3f3d000       Deferred        winepulse<elf> 
  \-PE  b3f20000-b3f3d000       \               winepulse 
ELF     b3f3d000-b3f61000       Deferred        mmdevapi<elf> 
  \-PE  b3f40000-b3f61000       \               mmdevapi 
ELF     b3f61000-b3f99000       Deferred        uxtheme<elf> 
  \-PE  b3f70000-b3f99000       \               uxtheme 
ELF     b3f99000-b4013000       Deferred        shlwapi<elf> 
  \-PE  b3fb0000-b4013000       \               shlwapi 
ELF     b4013000-b411f000       Deferred        comctl32<elf> 
  \-PE  b4020000-b411f000       \               comctl32 
ELF     b411f000-b414b000       Deferred        msvfw32<elf> 
  \-PE  b4120000-b414b000       \               msvfw32 
ELF     b414b000-b4197000       Deferred        dsound<elf> 
  \-PE  b4150000-b4197000       \               dsound 
ELF     b41a2000-b41e0000       Deferred        d3d9<elf> 
  \-PE  b41b0000-b41e0000       \               d3d9 
ELF     b41e0000-b4291000       Deferred        msvcrt<elf> 
  \-PE  b4200000-b4291000       \               msvcrt 
ELF     b4291000-b42bc000       Deferred        msacm32<elf> 
  \-PE  b42a0000-b42bc000       \               msacm32 
ELF     b42bc000-b4375000       Deferred        winmm<elf> 
  \-PE  b42c0000-b4375000       \               winmm 
ELF     b4375000-b439d000       Deferred        devenum<elf> 
  \-PE  b4380000-b439d000       \               devenum 
ELF     b467a000-b468f000       Deferred        avicap32<elf> 
  \-PE  b4680000-b468f000       \               avicap32 
ELF     b4a50000-b6756000       Deferred        libnvidia-glcore.so.304.125 
ELF     b6756000-b675a000       Deferred        libnvidia-tls.so.304.125 
ELF     b675a000-b6836000       Deferred        libgl.so.1 
ELF     b6836000-b6840000       Deferred        libffi.so.6 
ELF     b6840000-b6859000       Deferred        libresolv.so.2 
ELF     b6859000-b685e000       Deferred        libkeyutils.so.1 
ELF     b685e000-b68b5000       Deferred        libdbus-1.so.3 
ELF     b68b5000-b6941000       Deferred        libgmp.so.10 
ELF     b6941000-b6970000       Deferred        libhogweed.so.2 
ELF     b6970000-b69a6000       Deferred        libnettle.so.4 
ELF     b69a6000-b69ba000       Deferred        libtasn1.so.6 
ELF     b69ba000-b69fe000       Deferred        libp11-kit.so.0 
ELF     b69fe000-b6a0b000       Deferred        libkrb5support.so.0 
ELF     b6a0b000-b6a10000       Deferred        libcom_err.so.2 
ELF     b6a10000-b6a42000       Deferred        libk5crypto.so.3 
ELF     b6a42000-b6b15000       Deferred        libkrb5.so.3 
ELF     b6b15000-b6b29000       Deferred        libavahi-client.so.3 
ELF     b6b29000-b6b37000       Deferred        libavahi-common.so.3 
ELF     b6b37000-b6c77000       Deferred        libgnutls-deb0.so.28 
ELF     b6c77000-b6cc7000       Deferred        libgssapi_krb5.so.2 
ELF     b6cc7000-b6d4c000       Deferred        libcups.so.2 
ELF     b6d71000-b6dab000       Deferred        ws2_32<elf> 
  \-PE  b6d80000-b6dab000       \               ws2_32 
ELF     b6dab000-b6dd3000       Deferred        dxgi<elf> 
  \-PE  b6db0000-b6dd3000       \               dxgi 
ELF     b6dd3000-b6dfa000       Deferred        iphlpapi<elf> 
  \-PE  b6de0000-b6dfa000       \               iphlpapi 
ELF     b6dfa000-b6e3d000       Deferred        winspool<elf> 
  \-PE  b6e00000-b6e3d000       \               winspool 
ELF     b6e3d000-b6e75000       Deferred        wbemprox<elf> 
  \-PE  b6e40000-b6e75000       \               wbemprox 
ELF     b6e89000-b6eff000       Deferred        ddraw<elf> 
  \-PE  b6e90000-b6eff000       \               ddraw 
ELF     b6eff000-b704d000       Deferred        wined3d<elf> 
  \-PE  b6f10000-b704d000       \               wined3d 
ELF     b705c000-b7084000       Deferred        d3dxof<elf> 
  \-PE  b7060000-b7084000       \               d3dxof 
ELF     b7084000-b709e000       Deferred        d3dx9_31<elf> 
  \-PE  b7090000-b709e000       \               d3dx9_31 
ELF     b709e000-b70b2000       Deferred        psapi<elf> 
  \-PE  b70a0000-b70b2000       \               psapi 
ELF     b7110000-b7117000       Deferred        libxfixes.so.3 
ELF     b7117000-b7122000       Deferred        libxcursor.so.1 
ELF     b7122000-b7134000       Deferred        libxi.so.6 
ELF     b7134000-b7138000       Deferred        libxcomposite.so.1 
ELF     b7138000-b7143000       Deferred        libxrandr.so.2 
ELF     b7143000-b714f000       Deferred        libxrender.so.1 
ELF     b714f000-b7155000       Deferred        libxxf86vm.so.1 
ELF     b7155000-b7177000       Deferred        libxcb.so.1 
ELF     b7177000-b72c2000       Deferred        libx11.so.6 
ELF     b72c2000-b72d7000       Deferred        libxext.so.6 
ELF     b72fc000-b7390000       Deferred        winex11<elf> 
  \-PE  b7310000-b7390000       \               winex11 
ELF     b739c000-b7557000       Dwarf           libc.so.6 
ELF     b7557000-b755c000       Deferred        libdl.so.2 
ELF     b755d000-b757a000       Deferred        libpthread.so.0 
ELF     b7581000-b7585000       Deferred        libxinerama.so.1 
ELF     b7585000-b758c000       Deferred        libxdmcp.so.6 
ELF     b758c000-b7590000       Deferred        libxau.so.6 
ELF     b7595000-b759f000       Deferred        libnss_compat.so.2 
ELF     b759f000-b7755000       Dwarf           libwine.so.1 
ELF     b7757000-b777b000       Deferred        ld-linux.so.2 
ELF     b777d000-b777e000       Deferred        [vdso].so 
Threads: 
process  tid      prio (all id:s are in hex) 
00000008 winecfg.exe 
        00000009    0 
0000000e services.exe 
        0000001e    0 
        0000001c    0 
        00000014    0 
        00000010    0 
        0000000f    0 
00000012 winedevice.exe 
        0000001b    0 
        00000018    0 
        00000017    0 
        00000013    0 
00000019 plugplay.exe 
        0000001f    0 
        0000001d    0 
        0000001a    0 
00000020 explorer.exe 
        00000024    0 
        00000023    0 
        00000022    0 
        00000021    0 
00000025 (D) Z:\media\leo\DATOS\Juegos XP\Evochron.Mercenary.v2.848.wth-keygen-THETA\EvochronMercenary.exe 
        0000002b    0 
        0000002a    0 
        00000029    0 
        00000028    0 
        00000027   15 
        00000026    0 <==
[/FONT]

```

Using a decompiler (and reading tons of documentation of decompiler language) i've found that the source tries to do in that address: "MOV DWORD ptr[ESI], EAX". If you need more info i will give it to you, since i can't understand why (and what tries to do) in that line it produces that error.

*In the second hand, when i put msvcp71 as native, the program runs but generates a window that says "Runtime Error 105 - File does not exist at line 147" and close. The output is:

```
 [FONT=monospace][COLOR=#000000]wine /media/leo/DATOS/Juegos\ XP/Evochron.Mercenary.v2.848.wth-keygen-THETA/EvochronMercenary.exe  [/COLOR]
fixme:ole:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046} 
err:winediag:wined3d_dll_init The GLSL shader backend has been disabled. You get to keep all the pieces if it breaks. 
fixme:wbemprox:wbem_services_CreateInstanceEnum unsupported flags 0x00000030 
fixme:wbemprox:enum_class_object_Next timeout not supported 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no fallback
 specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no fallback
 specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32G32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32G32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32G32B32A32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no
 fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32G32B32A32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no
 fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no fallback
 specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no fallback
 specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16B16A16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no
 fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16B16A16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no
 fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8A8_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fal
lback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8A8_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fal
lback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8X8_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fal
lback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8X8_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fal
lback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B5G6R5_UNORM rtInternal format is not supported as FBO color attachment, type 0. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B5G6R5_UNORM rtInternal format is not supported as FBO color attachment, type 2. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fallback 
specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 1), and no fallback 
specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fallback 
specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 3), and no fallback 
specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R10G10B10A2_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no 
fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R10G10B10A2_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no 
fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8G8B8A8_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fal
lback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8G8B8A8_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fal
lback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B10G10R10A2_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no 
fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B10G10R10A2_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no 
fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16B16A16_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no
 fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16B16A16_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no
 fallback specified. 
fixme:win:EnumDisplayDevicesW ((null),0,0xe2d1f8,0x00000000), stub! 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no fallback
 specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no fallback
 specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32G32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32G32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32G32B32A32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no
 fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32G32B32A32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no
 fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no fallback
 specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no fallback
 specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16B16A16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no
 fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16B16A16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no
 fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8A8_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fal
lback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8A8_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fal
lback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8X8_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fal
lback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8X8_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fal
lback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B5G6R5_UNORM rtInternal format is not supported as FBO color attachment, type 0. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B5G6R5_UNORM rtInternal format is not supported as FBO color attachment, type 2. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fallback 
specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 1), and no fallback 
specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fallback 
specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 3), and no fallback 
specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R10G10B10A2_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no 
fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R10G10B10A2_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no 
fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8G8B8A8_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fal
lback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8G8B8A8_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fal
lback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B10G10R10A2_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no 
fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B10G10R10A2_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no 
fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16B16A16_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no
 fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16B16A16_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no
 fallback specified. 
fixme:win:EnumDisplayDevicesW ((null),0,0xe2cfe8,0x00000000), stub! 
fixme:ddraw:ddraw7_Initialize Ignoring guid {aeb2cdd4-6e41-43ea-941c-8361cc760781}. 
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {33d9a761-90c8-11d0-bd43-00a0c911ce86} not found 
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found 
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no fallback
 specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no fallback
 specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32G32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32G32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32G32B32A32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no
 fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32G32B32A32_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no
 fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no fallback
 specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no fallback
 specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16B16A16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 0), and no
 fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16B16A16_FLOAT with rendertarget flag is not supported as FBO color attachment (type 2), and no
 fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8A8_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fal
lback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8A8_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fal
lback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8X8_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fal
lback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8X8_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fal
lback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B5G6R5_UNORM rtInternal format is not supported as FBO color attachment, type 0. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B5G6R5_UNORM rtInternal format is not supported as FBO color attachment, type 2. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fallback 
specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 1), and no fallback 
specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fallback 
specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8_UNORM with rendertarget flag is not supported as FBO color attachment (type 3), and no fallback 
specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R10G10B10A2_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no 
fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R10G10B10A2_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no 
fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8G8B8A8_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fal
lback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R8G8B8A8_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fal
lback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no fallb
ack specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B10G10R10A2_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no 
fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_B10G10R10A2_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no 
fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16B16A16_UNORM with rendertarget flag is not supported as FBO color attachment (type 0), and no
 fallback specified. 
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16B16A16_UNORM with rendertarget flag is not supported as FBO color attachment (type 2), and no
 fallback specified. 
fixme:win:EnumDisplayDevicesW ((null),0,0xe2e3e8,0x00000000), stub! 
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered 
err:ole:CoGetClassObject class {96749377-3391-11d2-9ee3-00c04f797396} not registered 
err:ole:create_server class {96749377-3391-11d2-9ee3-00c04f797396} not registered 
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported 
err:ole:CoGetClassObject no class object {96749377-3391-11d2-9ee3-00c04f797396} could be created for context 0x17 
fixme:msvcrt:__clean_type_info_names_internal (0xcee3344) stub
[/FONT]

```

I can't understand/identify what exactly is that missing file, but this has got a particularity: when i run with msvcp71 as native in the decompiler the program runs without that message window and continues, but when the game has to generate planets data or generate the universe it crashes with an unhandled exception. I Haven't found what produces this exception.

The decompiler i've used in wine is GoVest!

All of this i've done with the recommendation that said an user in [https://appdb.winehq.org/objectManager.php?sClass=version&iId=27779](https://appdb.winehq.org/objectManager.php?sClass=version&iId=27779) of use dinput8.dll as native because the game hangs-up after show a window with builtin dinput8 (it's a known bug)

The wine version is 1.7.44 running with mono 4.5.4 (the version of mono is relevant?); and running in:
Kubuntu 15.04 32bit  with linux kernel 3.19.0-25-generic (Metacity desktop session if relevant)
Vcard: Nvidia 6200 AGP 512Mb vram (that is why i've disabled the GLSL support)
Ram 1.2Gb Swap 2Gb

Regards!

---

