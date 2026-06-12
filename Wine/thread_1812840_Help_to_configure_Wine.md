---
title: "Help to configure Wine"
date: 2011-07-26
forum: Wine
---

### Post by Dakeru on 2011-07-26
Hi, I wish someone can help me with this.
I'm using Natty and I installed Wine ($ sudo apt-get install wine) and it didnt show any error, but when i want to configure it ($ winecfg) the following error happens:

```
dakeru@dakeru-VPCEB13EL:~$ winecfg
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\services.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\services.exe" failed, status c0000135
err:wineboot:start_services_process Unexpected termination of services.exe - exit code -1073741515
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\ole32.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"C:\\windows\\system32\\winemenubuilder.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\winemenubuilder.exe" failed, status c0000135
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\ole32.dll") not found
err:module:DelayLoadFailureHook failed to delay load ole32.dll.CoTaskMemAlloc
wine: Call from 0x7b835cc2 to unimplemented function ole32.dll.CoTaskMemAlloc, aborting
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100
err:module:DelayLoadFailureHook failed to delay load shell32.dll.SHGetFolderPathW
wine: Call from 0x7b835cc2 to unimplemented function shell32.dll.SHGetFolderPathW, aborting
wine: Unimplemented function shell32.dll.SHGetFolderPathW called at address 0x7b835cc2 (thread 000b), starting debugger...
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\explorer.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\explorer.exe" failed, status c0000135
Unhandled exception: unimplemented function shell32.dll.SHGetFolderPathW called in 32-bit code (0x7b835cc2).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b835cc2 ESP:0033f874 EBP:0033f8d8 EFLAGS:00000203(   - --  I   - - -C)
 EAX:7b824eb9 EBX:7b882ff4 ECX:683228dc EDX:0033f894
 ESI:80000100 EDI:683228dc
Stack dump:
0x0033f874:  0033f908 00000008 68321ff4 80000100
0x0033f884:  00000001 00000000 7b835cc2 00000002
0x0033f894:  683228dc 6832291e 68022cb7 00000001
0x0033f8a4:  7b97aa60 7b87b407 7b87b36f 0033f8f0
0x0033f8b4:  00000020 0033f918 6831a6b1 3bfc0000
0x0033f8c4:  68322964 000c000b 7b835c7a 7b882ff4
Backtrace:
=>0 0x7b835cc2 in kernel32 (+0x25cc2) (0x0033f8d8)
  1 0x7b84ef3b DelayLoadFailureHook+0x5a() in kernel32 (0x0033f928)
  2 0x6831a731 in wineboot (+0xa730) (0x0033f988)
  3 0x68316008 in wineboot (+0x6007) (0x0033fc38)
  4 0x683196f0 main+0x6ff() in wineboot (0x0033fe48)
  5 0x6831a80c in wineboot (+0xa80b) (0x0033fe90)
  6 0x7b85437c call_process_entry+0xb() in kernel32 (0x0033fea8)
  7 0x7b85501f ExitProcess+0xc9e() in kernel32 (0x0033fee8)
  8 0x7bc70be0 call_thread_func+0xb() in ntdll (0x0033fef8)
  9 0x7bc73770 call_thread_entry_point+0x6f() in ntdll (0x0033ffc8)
  10 0x7bc498ba call_dll_entry_point+0x659() in ntdll (0x0033ffe8)
0x7b835cc2: subl    $4,%esp
Modules:
Module    Address            Debug info    Name (48 modules)
ELF    20000000-2008b000    Deferred        gdi32<elf>
  \-PE    20010000-2008b000    \               gdi32
ELF    20178000-20219000    Deferred        winex11<elf>
  \-PE    20190000-20219000    \               winex11
ELF    20219000-2023a000    Deferred        imm32<elf>
  \-PE    20220000-2023a000    \               imm32
ELF    2023a000-2023e000    Deferred        libxinerama.so.1
ELF    2023e000-20244000    Deferred        libxxf86vm.so.1
ELF    20244000-2024c000    Deferred        libxrandr.so.2
ELF    2024c000-20256000    Deferred        libxcursor.so.1
ELF    216b0000-216c9000    Deferred        libxcb.so.1
ELF    39bcb000-39be0000    Deferred        libz.so.1
ELF    3bfb7000-3c018000    Deferred        shlwapi<elf>
  \-PE    3bfc0000-3c018000    \               shlwapi
ELF    3c8ac000-3c932000    Deferred        libfreetype.so.6
ELF    3df68000-3e09a000    Deferred        user32<elf>
  \-PE    3df80000-3e09a000    \               user32
ELF    40ae1000-40ae7000    Deferred        libxfixes.so.3
ELF    41720000-4174f000    Deferred        libfontconfig.so.1
ELF    48d9e000-48da3000    Deferred        libuuid.so.1
ELF    4dec0000-4deca000    Deferred        libxrender.so.1
ELF    4fa58000-4fb73000    Deferred        libx11.so.6
ELF    58fd2000-58fd6000    Deferred        libxau.so.6
ELF    5be88000-5beb2000    Deferred        libexpat.so.1
ELF    68000000-6801e000    Deferred        ld-linux.so.2
ELF    6801e000-6815e000    Export          libwine.so.1
ELF    6815e000-682bf000    Deferred        libc.so.6
ELF    682bf000-682e5000    Deferred        libm.so.6
ELF    682e5000-682ed000    Deferred        libnss_compat.so.2
ELF    682ed000-68304000    Deferred        libnsl.so.1
ELF    68304000-68328000    Export          wineboot<elf>
  \-PE    68310000-68328000    \               wineboot
ELF    69ccd000-69cd9000    Deferred        libnss_files.so.2
ELF    6b6ae000-6b6b6000    Deferred        libsm.so.6
ELF    6f739000-6f748000    Deferred        libxext.so.6
ELF    70d56000-70d6f000    Deferred        libpthread.so.0
ELF    70fd1000-70fd7000    Deferred        libxdmcp.so.6
ELF    716d5000-716e0000    Deferred        libnss_nis.so.2
ELF    73ce6000-73cea000    Deferred        libxcomposite.so.1
ELF    77b3b000-77b3f000    Deferred        libdl.so.2
ELF    77e32000-77e4a000    Deferred        libice.so.6
ELF    7b800000-7b97c000    Export          kernel32<elf>
  \-PE    7b810000-7b97c000    \               kernel32
ELF    7bc00000-7bcba000    Export          ntdll<elf>
  \-PE    7bc10000-7bcba000    \               ntdll
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7cac9000-7cb23000    Deferred        advapi32<elf>
  \-PE    7cad0000-7cb23000    \               advapi32
Threads:
process  tid      prio (all id:s are in hex)
00000008 ntdll.dll
    00000009    0
0000000a (D) C:\windows\system32\wineboot.exe
    0000000b    0 <==
Backtrace:
=>0 0x7b835cc2 in kernel32 (+0x25cc2) (0x0033f8d8)
  1 0x7b84ef3b DelayLoadFailureHook+0x5a() in kernel32 (0x0033f928)
  2 0x6831a731 in wineboot (+0xa730) (0x0033f988)
  3 0x68316008 in wineboot (+0x6007) (0x0033fc38)
  4 0x683196f0 main+0x6ff() in wineboot (0x0033fe48)
  5 0x6831a80c in wineboot (+0xa80b) (0x0033fe90)
  6 0x7b85437c call_process_entry+0xb() in kernel32 (0x0033fea8)
  7 0x7b85501f ExitProcess+0xc9e() in kernel32 (0x0033fee8)
  8 0x7bc70be0 call_thread_func+0xb() in ntdll (0x0033fef8)
  9 0x7bc73770 call_thread_entry_point+0x6f() in ntdll (0x0033ffc8)
  10 0x7bc498ba call_dll_entry_point+0x659() in ntdll (0x0033ffe8)
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\ole32.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"C:\\windows\\system32\\winecfg.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\winecfg.exe" failed, status c0000135
```I hope someone can repply, i had checked every site I found but I got nothing, tnx..

---

### Post by wineman on 2011-07-28
basically your wine is crashing as it loads. what you need to do is purge it (apt-get purge wine), then install the latest stable version in the wine repository (see [http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu) for more or execute `sudo add-apt-repository ppa:ubuntu-wine/ppa`).

The actual error in your wine system is this: your GDI has been tampered with and needs to be repaired. This can be done by redoing the wine cache (rm -rf ~/.wine && env WINEPREFIX=~/.wine wine notepad), and then run an app in that repo (env WINEPREFIX=~/.wine wine <program path>) - this error is in gdi32.dll relating to the services.exe app, which i think might have messed up your system.

---

### Post by lailokenwiz on 2011-07-29
> **wineman said:**
> basically your wine is crashing as it loads. what you need to do is purge it (apt-get purge wine), then install the latest stable version in the wine repository (see [http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu) for more or execute `sudo add-apt-repository ppa:ubuntu-wine/ppa`).

The actual error in your wine system is this: your GDI has been tampered with and needs to be repaired. This can be done by redoing the wine cache (rm -rf ~/.wine && env WINEPREFIX=~/.wine wine notepad), and then run an app in that repo (env WINEPREFIX=~/.wine wine <program path>) - this error is in gdi32.dll relating to the services.exe app, which i think might have messed up your system.
But all I hear is "Reinstall, reinstall, reinstall"

---

### Post by cwwilson721 on 2011-07-29
NO.

The poster said "purge it", then reinstall.

---

