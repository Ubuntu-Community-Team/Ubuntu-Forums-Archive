---
title: "Hitman Blood Money &quot;error&quot;"
date: 2008-05-24
forum: Wine
---

### Post by JLoomis95 on 2008-05-24
I think i found the issue but i have no clue how to fix it. The game crashes when i try to change the graphic settings. here is what the terminal says:
```
]
fixme:spoolsv:serv_main (0 (nil))
[email]justin@desktop:~/.wine[/email]/drive_c/Program Files/Eidos/Hitman Blood Money$ wine configure.exe 
fixme:spoolsv:serv_main (0 (nil))
fixme:win:EnumDisplayDevicesW ((null),0,0x33e210,0x00000000), stub!
[email]justin@desktop:~/.wine[/email]/drive_c/Program Files/Eidos/Hitman Blood Money$ fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (-6,-25)-(1030,774)
fixme:win:EnumDisplayDevicesW ((null),0,0x155ed7c,0x00000000), stub!
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (21,846)-(53,878)
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (-6,-25)-(106,6)
wine: Unhandled page fault on write access to 0x00000000 at address 0x1c7e7b02 (thread 001f), starting debugger...
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x1c7e7b02).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:1c7e7b02 ESP:0155f204 EBP:0155f210 EFLAGS:00010202(   - 00      - -RI1)
 EAX:1c7e7b00 EBX:7ec14ff4 ECX:1ed2c018 EDX:1fd03970
 ESI:1ed2c018 EDI:00000000
Stack dump:
0x0155f204:  7eb8dfb5 1c7e7b00 1ed2c018 0155f240
0x0155f214:  7ebad3e2 1ed2c018 0155f274 7bc7471b
0x0155f224:  7bc8843c 13810020 13810000 7ebad61b
0x0155f234:  7ec48ed0 7ec48ed0 1ed2c018 0155f330
0x0155f244:  7ec2f7b9 1ed2c018 0155f274 134f00e0
0x0155f254:  7bc8843c 134f00e0 00000080 0155f2b0
Backtrace:
=>1 0x1c7e7b02 (0x0155f210)
  2 0x7ebad3e2 IWineD3DBaseSurfaceImpl_GetParent+0x32() in wined3d (0x0155f240)
  3 0x7ec2f7b9 in d3d9 (+0xf7b9) (0x0155f330)
  4 0x7eb650fa in wined3d (+0x350fa) (0x0155f370)
  5 0x7ec2f9d2 in d3d9 (+0xf9d2) (0x0155f400)
  6 0x0048f78e in hitmanbloodmoney (+0x8f78e) (0x00000000)
0x1c7e7b02: rcrb        $1,0x0(%edi)
Modules:
Module  Address                 Debug info      Name (82 modules)
PE        400000- 135a000       Export          hitmanbloodmoney
PE       1560000- 17af000       Deferred        d3dx9_27
PE      30000000-3006d000       Deferred        binkw32
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca4000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca4000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
PE      7c340000-7c396000       Deferred        msvcr71
ELF     7cd50000-7cd99000       Deferred        dbghelp<elf>
  \-PE  7cd60000-7cd99000       \               dbghelp
ELF     7d3f9000-7d404000       Deferred        libgcc_s.so.1
ELF     7d407000-7d41c000       Deferred        psapi<elf>
  \-PE  7d410000-7d41c000       \               psapi
ELF     7d787000-7e00d000       Deferred        libglcore.so.1
ELF     7e00d000-7e099000       Deferred        libgl.so.1
ELF     7e33b000-7e35a000       Deferred        imm32<elf>
  \-PE  7e340000-7e35a000       \               imm32
ELF     7e35a000-7e36f000       Deferred        midimap<elf>
  \-PE  7e360000-7e36f000       \               midimap
ELF     7e36f000-7e395000       Deferred        msacm32<elf>
  \-PE  7e380000-7e395000       \               msacm32
ELF     7e395000-7e45b000       Deferred        libasound.so.2
ELF     7e45b000-7e473000       Deferred        msacm32<elf>
  \-PE  7e460000-7e473000       \               msacm32
ELF     7e473000-7e4a9000       Deferred        winealsa<elf>
  \-PE  7e480000-7e4a9000       \               winealsa
ELF     7e507000-7e50c000       Deferred        libxfixes.so.3
ELF     7e50c000-7e515000       Deferred        libxcursor.so.1
ELF     7e515000-7e51b000       Deferred        libxrandr.so.2
ELF     7e51b000-7e523000       Deferred        libxrender.so.1
ELF     7e523000-7e526000       Deferred        libxinerama.so.1
ELF     7e526000-7e52b000       Deferred        libxdmcp.so.6
ELF     7e52b000-7e52e000       Deferred        libxau.so.6
ELF     7e52e000-7e61f000       Deferred        libx11.so.6
ELF     7e61f000-7e62d000       Deferred        libxext.so.6
ELF     7e631000-7e633000       Deferred        libnvidia-tls.so.1
ELF     7e645000-7e6d2000       Deferred        winex11<elf>
  \-PE  7e650000-7e6d2000       \               winex11
ELF     7e75a000-7e77a000       Deferred        libexpat.so.1
ELF     7e77a000-7e7a5000       Deferred        libfontconfig.so.1
ELF     7e7a5000-7e7ba000       Deferred        libz.so.1
ELF     7e7ba000-7e82a000       Deferred        libfreetype.so.6
ELF     7e82a000-7e855000       Deferred        ws2_32<elf>
  \-PE  7e830000-7e855000       \               ws2_32
ELF     7e855000-7e8bb000       Deferred        msvcrt<elf>
  \-PE  7e860000-7e8bb000       \               msvcrt
ELF     7e8bb000-7e948000       Deferred        winmm<elf>
  \-PE  7e8d0000-7e948000       \               winmm
ELF     7e948000-7e993000       Deferred        dsound<elf>
  \-PE  7e950000-7e993000       \               dsound
ELF     7e993000-7e9a6000       Deferred        libresolv.so.2
ELF     7e9be000-7e9dc000       Deferred        iphlpapi<elf>
  \-PE  7e9c0000-7e9dc000       \               iphlpapi
ELF     7e9dc000-7ea3c000       Deferred        rpcrt4<elf>
  \-PE  7e9f0000-7ea3c000       \               rpcrt4
ELF     7ea3c000-7eadf000       Deferred        ole32<elf>
  \-PE  7ea50000-7eadf000       \               ole32
ELF     7eadf000-7eb16000       Deferred        dinput<elf>
  \-PE  7eaf0000-7eb16000       \               dinput
ELF     7eb16000-7ec19000       Export          wined3d<elf>
  \-PE  7eb30000-7ec19000       \               wined3d
ELF     7ec19000-7ec4a000       Export          d3d9<elf>
  \-PE  7ec20000-7ec4a000       \               d3d9
ELF     7ec4a000-7ec9a000       Deferred        advapi32<elf>
  \-PE  7ec60000-7ec9a000       \               advapi32
ELF     7ec9a000-7ed34000       Deferred        gdi32<elf>
  \-PE  7ecb0000-7ed34000       \               gdi32
ELF     7ed34000-7ee78000       Deferred        user32<elf>
  \-PE  7ed50000-7ee78000       \               user32
ELF     7ee78000-7ee83000       Deferred        libnss_files.so.2
ELF     7ee83000-7ee8c000       Deferred        libnss_compat.so.2
ELF     7ee8c000-7eea4000       Deferred        dinput8<elf>
  \-PE  7ee90000-7eea4000       \               dinput8
ELF     7efc3000-7efe8000       Deferred        libm.so.6
ELF     7efe8000-7f000000       Deferred        libnsl.so.1
ELF     f7cea000-f7cee000       Deferred        libdl.so.2
ELF     f7cee000-f7e38000       Deferred        libc.so.6
ELF     f7e39000-f7e51000       Deferred        libpthread.so.0
ELF     f7e55000-f7e5f000       Deferred        libnss_nis.so.2
ELF     f7e69000-f7f7d000       Deferred        libwine.so.1
ELF     f7f7f000-f7f9d000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
        00000016    0
        0000000e    0
        0000000d    0
00000012 
        00000015    0
        00000014    0
        00000013    0
0000001c 
        0000001d    0
0000001e (D) C:\Program Files\Eidos\Hitman Blood Money\HitmanBloodMoney.exe
        00000023    2
        00000022    1
        00000021   15
        00000020    0
        0000001f    0 <==
Backtrace:
=>1 0x1c7e7b02 (0x0155f210)
  2 0x7ebad3e2 IWineD3DBaseSurfaceImpl_GetParent+0x32() in wined3d (0x0155f240)
  3 0x7ec2f7b9 in d3d9 (+0xf7b9) (0x0155f330)
  4 0x7eb650fa in wined3d (+0x350fa) (0x0155f370)
  5 0x7ec2f9d2 in d3d9 (+0xf9d2) (0x0155f400)
  6 0x0048f78e in hitmanbloodmoney (+0x8f78e) (0x00000000)

[email]justin@desktop:~/.wine[/email]/drive_c/Program Files/Eidos/Hitman Blood Money$ wine: Call from 0x7b841e20 to unimplemented function d3dx9_36.dl       ader, aborting
bash: wine:: command not found
[email]justin@desktop:~/.wine[/email]/drive_c/Program Files/Eidos/Hitman Blood Money$ wine Call from 0x7b841e20 to unimplemented function d3dx9_36.dl       ader, aborting
wine: could not load L"c:\\windows\\system32\\Call.exe": Module not found
[email]justin@desktop:~/.wine[/email]/drive_c/Program Files/Eidos/Hitman Blood Money$ fixme:spoolsv:serv_main (0 (nil))

[email]justin@desktop:~/.wine[/email]/drive_c/Program Files/Eidos/Hitman Blood Money$ ls
binkw32.dll    HitmanBloodMoney.exe      Movies       ReadMe.rtf
configure.exe  HitmanBloodMoney.exe.old  msvcr71.dll  Scenes
ENCVAG.DLL     HitmanBloodMoney.ini      pc_eng.str   Scriptcs
[email]justin@desktop:~/.wine[/email]/drive_c/Program Files/Eidos/Hitman Blood Money$ wine configure.exe 
fixme:spoolsv:serv_main (0 (nil))
fixme:win:EnumDisplayDevicesW ((null),0,0x33e210,0x00000000), stub!
[email]justin@desktop:~/.wine[/email]/drive_c/Program Files/Eidos/Hitman Blood Money$ fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (-6,-25)-(1030,774)
fixme:win:EnumDisplayDevicesW ((null),0,0x155ed7c,0x00000000), stub!
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_R16F
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (1,28)-(1037,827)
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (-6,-25)-(106,6)
wine: Unhandled page fault on write access to 0xfc78e03b at address 0x138284 (thread 001f), starting debugger...
Unhandled exception: page fault on write access to 0xfc78e03b in 32-bit code (0x00138284).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00138284 ESP:0155f200 EBP:0155f210 EFLAGS:00010297(   - 00     RISAP1C)
 EAX:00138280 EBX:7ec081f4 ECX:1c50e028 EDX:1ed2c780
 ESI:1c50e028 EDI:00000000
Stack dump:
0x0155f200:  0000002b 7eb83fb5 00138280 1c50e028
0x0155f210:  0155f240 7eba33e2 1c50e028 0155f274
0x0155f220:  7bc7471b 7bc8843c 13810020 13810000
0x0155f230:  7eba361b 7ec3eed0 7ec3eed0 1c50e028
0x0155f240:  0155f330 7ec257b9 1c50e028 0155f274
0x0155f250:  134f00e0 7bc8843c 134f00e0 00000080
Backtrace:
=>1 0x00138284 (0x0155f210)
  2 0x7eba33e2 IWineD3DBaseSurfaceImpl_GetParent+0x32() in wined3d (0x0155f240)
  3 0x7ec257b9 in d3d9 (+0x57b9) (0x0155f330)
  4 0x7eb5b0fa in wined3d (+0x3b0fa) (0x0155f370)
  5 0x7ec259d2 in d3d9 (+0x59d2) (0x0155f400)
  6 0x0048f78e in hitmanbloodmoney (+0x8f78e) (0x00000000)
0x00138284: rclb        $0x50,0xe0280013(%esi)
Modules:
Module  Address                 Debug info      Name (82 modules)
PE        400000- 135a000       Export          hitmanbloodmoney
PE       1560000- 17af000       Deferred        d3dx9_27
PE      30000000-3006d000       Deferred        binkw32
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bca4000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bca4000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
PE      7c340000-7c396000       Deferred        msvcr71
ELF     7cd3c000-7cd85000       Deferred        dbghelp<elf>
  \-PE  7cd40000-7cd85000       \               dbghelp
ELF     7d3e5000-7d3f0000       Deferred        libgcc_s.so.1
ELF     7d3f3000-7d408000       Deferred        psapi<elf>
  \-PE  7d400000-7d408000       \               psapi
ELF     7d773000-7dff9000       Deferred        libglcore.so.1
ELF     7dff9000-7e085000       Deferred        libgl.so.1
ELF     7e327000-7e346000       Deferred        imm32<elf>
  \-PE  7e330000-7e346000       \               imm32
ELF     7e346000-7e35b000       Deferred        midimap<elf>
  \-PE  7e350000-7e35b000       \               midimap
ELF     7e35b000-7e381000       Deferred        msacm32<elf>
  \-PE  7e360000-7e381000       \               msacm32
ELF     7e381000-7e447000       Deferred        libasound.so.2
ELF     7e447000-7e45f000       Deferred        msacm32<elf>
  \-PE  7e450000-7e45f000       \               msacm32
ELF     7e45f000-7e495000       Deferred        winealsa<elf>
  \-PE  7e470000-7e495000       \               winealsa
ELF     7e4f3000-7e4f8000       Deferred        libxfixes.so.3
ELF     7e4f8000-7e501000       Deferred        libxcursor.so.1
ELF     7e501000-7e507000       Deferred        libxrandr.so.2
ELF     7e507000-7e50f000       Deferred        libxrender.so.1
ELF     7e50f000-7e512000       Deferred        libxinerama.so.1
ELF     7e512000-7e517000       Deferred        libxdmcp.so.6
ELF     7e517000-7e51a000       Deferred        libxau.so.6
ELF     7e51a000-7e60b000       Deferred        libx11.so.6
ELF     7e60b000-7e619000       Deferred        libxext.so.6
ELF     7e631000-7e6be000       Deferred        winex11<elf>
  \-PE  7e640000-7e6be000       \               winex11
ELF     7e750000-7e770000       Deferred        libexpat.so.1
ELF     7e770000-7e79b000       Deferred        libfontconfig.so.1
ELF     7e79b000-7e7b0000       Deferred        libz.so.1
ELF     7e7b0000-7e820000       Deferred        libfreetype.so.6
ELF     7e820000-7e84b000       Deferred        ws2_32<elf>
  \-PE  7e830000-7e84b000       \               ws2_32
ELF     7e84b000-7e8b1000       Deferred        msvcrt<elf>
  \-PE  7e860000-7e8b1000       \               msvcrt
ELF     7e8b1000-7e93e000       Deferred        winmm<elf>
  \-PE  7e8c0000-7e93e000       \               winmm
ELF     7e93e000-7e989000       Deferred        dsound<elf>
  \-PE  7e950000-7e989000       \               dsound
ELF     7e989000-7e99c000       Deferred        libresolv.so.2
ELF     7e99c000-7e99e000       Deferred        libnvidia-tls.so.1
ELF     7e9b4000-7e9d2000       Deferred        iphlpapi<elf>
  \-PE  7e9c0000-7e9d2000       \               iphlpapi
ELF     7e9d2000-7ea32000       Deferred        rpcrt4<elf>
  \-PE  7e9e0000-7ea32000       \               rpcrt4
ELF     7ea32000-7ead5000       Deferred        ole32<elf>
  \-PE  7ea40000-7ead5000       \               ole32
ELF     7ead5000-7eb0c000       Deferred        dinput<elf>
  \-PE  7eae0000-7eb0c000       \               dinput
ELF     7eb0c000-7ec0f000       Export          wined3d<elf>
  \-PE  7eb20000-7ec0f000       \               wined3d
ELF     7ec0f000-7ec40000       Export          d3d9<elf>
  \-PE  7ec20000-7ec40000       \               d3d9
ELF     7ec40000-7ec90000       Deferred        advapi32<elf>
  \-PE  7ec50000-7ec90000       \               advapi32
ELF     7ec90000-7ed2a000       Deferred        gdi32<elf>
  \-PE  7eca0000-7ed2a000       \               gdi32
ELF     7ed2a000-7ee6e000       Deferred        user32<elf>
  \-PE  7ed40000-7ee6e000       \               user32
ELF     7ee6e000-7ee79000       Deferred        libnss_files.so.2
ELF     7ee79000-7ee83000       Deferred        libnss_nis.so.2
ELF     7ee83000-7ee8c000       Deferred        libnss_compat.so.2
ELF     7ee8c000-7eea4000       Deferred        dinput8<elf>
  \-PE  7ee90000-7eea4000       \               dinput8
ELF     7efc3000-7efe8000       Deferred        libm.so.6
ELF     7efe8000-7f000000       Deferred        libnsl.so.1
ELF     f7d18000-f7d1c000       Deferred        libdl.so.2
ELF     f7d1c000-f7e66000       Deferred        libc.so.6
ELF     f7e67000-f7e7f000       Deferred        libpthread.so.0
ELF     f7e97000-f7fab000       Deferred        libwine.so.1
ELF     f7fad000-f7fcb000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000c 
        00000016    0
        0000000e    0
        0000000d    0
00000012 
        00000015    0
        00000014    0
        00000013    0
0000001c 
        0000001d    0
0000001e (D) C:\Program Files\Eidos\Hitman Blood Money\HitmanBloodMoney.exe
        00000023    2
        00000022    1
        00000021   15
        00000020    0
        0000001f    0 <==
Backtrace:
=>1 0x00138284 (0x0155f210)
  2 0x7eba33e2 IWineD3DBaseSurfaceImpl_GetParent+0x32() in wined3d (0x0155f240)
  3 0x7ec257b9 in d3d9 (+0x57b9) (0x0155f330)
  4 0x7eb5b0fa in wined3d (+0x3b0fa) (0x0155f370)
  5 0x7ec259d2 in d3d9 (+0x59d2) (0x0155f400)
  6 0x0048f78e in hitmanbloodmoney (+0x8f78e) (0x00000000)
```

Any help would be nice thanks.

---

