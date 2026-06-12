---
title: "Odin maplestory."
date: 2008-06-06
forum: Wine
---

### Post by Takebacker on 2008-06-06
Well, most of us know that maplestory is a pain in the *** to get running (try impossible) however odinms doesn't use gameguard which gives us most of the trouble. Would anyone know how to get odin working with wine?

---

### Post by cogadh on 2008-06-06
I would guess that all you really need to do is download the Odin client and install it in Wine like you would any other software:
[http://odinms-status.info/](http://odinms-status.info/)

---

### Post by Takebacker on 2008-06-06
> **cogadh said:**
> I would guess that all you really need to do is download the Odin client and install it in Wine like you would any other software:
[http://odinms-status.info/](http://odinms-status.info/)

Well, i installed the full installer and everything is in it's own folder but i run the .exe and it freezes before the login screen. I guess i'll check guides and stuff on how to work wine.

---

### Post by Takebacker on 2008-06-09
Kind of a bump. :P

I was wondering if anyone here could tell me a few things.
1) If i wanted to run a program what command would i use to run it? I think it's "wine *insert directory here*" right?
2) If i right clicked the .exe, and chose to run it in wine and then the window comes up and it doesn't respond when it gets to the log-in screen what would you suggest i do?

---

### Post by cogadh on 2008-06-09
Until you get the app working perfectly (or at least good enough), you should run it from the terminal only. That way you can get informative error messages from Wine for troubleshooting purposes. The best way to run something in Wine from the terminal is by changing directories to the applcaition's install directory, then "wine"ing the executable:
```
cd ~/.wine/drive_c/Program\ Files/<application directory>
wine <application executable>.exe
```
As for the problem you are having, after you run it from the terminal, post the output here, we may be able to come up with something helpful.

---

### Post by Takebacker on 2008-06-10
Why do i have a feeling it has something to do with having the most recent version of wine. Oh well, i'm downloading it now but it's 1:30 am so i'm gonna go to bed. I'll post tomorrow with my results.

---

### Post by Takebacker on 2008-06-10
Ok, here's the output. Seems like there are a lot of errors. >_>

```

takebacker@takebacker-laptop:~$ wine OdinMS.exe
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on Intel ICH6 Modem, disabling mixer
fixme:win:EnumDisplayDevicesW ((null),0,0x33f3d0,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:imm:ImmGetDefaultIMEWnd (0x10026 - (nil) 0x132390 ): semi-stub
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\windows\\system32\\WzFlashRenderer.dll") not found
fixme:wininet:FtpGetFileSize (0x3, (nil))
fixme:dsound:IDirectSoundBufferImpl_Restore (0x3f368068):stub
fixme:dsound:IDirectSoundBufferImpl_Restore (0x3f48f758):stub
wine: Call from 0x7b840fc8 to unimplemented function ntoskrnl.exe.IoGetCurrentProcess, aborting
wine: Unimplemented function ntoskrnl.exe.IoGetCurrentProcess called at address 0x7b840fc8 (thread 0024), starting debugger...
Unhandled exception: unimplemented function ntoskrnl.exe.IoGetCurrentProcess called in 32-bit code (0x7b841042).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b841042 ESP:7ecce858 EBP:7ecce8bc EFLAGS:00000212(   - 00      - -IA1)
 EAX:7b82c171 EBX:7b8ac8a0 ECX:00000000 EDX:7ecce8d4
 ESI:7ecce8d4 EDI:004500d0
Stack dump:
0x7ecce858:  7ecce8d4 00000008 00450000 80000100
0x7ecce868:  00000001 00000000 7b840fc8 00000002
0x7ecce878:  7ee00640 7ee0265c 00000128 7ecce8b0
0x7ecce888:  7ecce8c8 7b842ae3 7ffd0bf8 7ecce8b0
0x7ecce898:  7b862f14 7bc40be1 7ffd0c00 7ecce8b8
0x7ecce8a8:  00110014 7bc32fe9 7b840fd2 7ee7b960
Backtrace:
=>1 0x7b841042 RaiseException+0x7a() in kernel32 (0x7ecce8bc)
  2 0x7ee005dd in ntoskrnl (+0x105dd) (0x7ecce8dc)
  3 0x7edf8c38 in ntoskrnl (+0x8c38) (0x7ecce9c8)
  4 0x7ee50c0d in advapi32 (+0x30c0d) (0x7eccea18)
  5 0x7bc684c6 call_thread_entry_point+0xe() in ntdll (0x7eccea28)
  6 0x7bc6927d in ntdll (+0x5927d) (0x7eccead8)
  7 0x7bc69d24 NtQueueApcThread() in ntdll (0x7eccf3d8)
  8 0xb7e5146b start_thread+0xcb() in libpthread.so.0 (0x7eccf4c8)
  9 0xb7dd46de __clone+0x5e() in libc.so.6 (0x00000000)
0x7b841042 RaiseException+0x7a in kernel32: subl        $4,%esp
Modules:
Module  Address                 Debug info      Name (31 modules)
PE        450000-  455400       Deferred        npkcrypt.sys
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bca2000       Export          ntdll<elf>
  \-PE  7bc10000-7bca2000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7eab6000-7eacb000       Deferred        hal<elf>
  \-PE  7eac0000-7eacb000       \               hal
ELF     7eacb000-7eb30000       Deferred        msvcrt<elf>
  \-PE  7eae0000-7eb30000       \               msvcrt
ELF     7eb30000-7eb43000       Deferred        libresolv.so.2
ELF     7eb43000-7eb61000       Deferred        iphlpapi<elf>
  \-PE  7eb50000-7eb61000       \               iphlpapi
ELF     7eb61000-7ebbf000       Deferred        rpcrt4<elf>
  \-PE  7eb70000-7ebbf000       \               rpcrt4
ELF     7ede1000-7ee19000       Export          ntoskrnl<elf>
  \-PE  7edf0000-7ee19000       \               ntoskrnl
ELF     7ee19000-7ee68000       Export          advapi32<elf>
  \-PE  7ee20000-7ee68000       \               advapi32
ELF     7ee68000-7ee7c000       Deferred        winedevice<elf>
  \-PE  7ee70000-7ee7c000       \               winedevice
ELF     7ee7c000-7ee87000       Deferred        libnss_files.so.2
ELF     7ee87000-7ee9f000       Deferred        libnsl.so.1
ELF     7ee9f000-7eea8000       Deferred        libnss_compat.so.2
ELF     7efd1000-7eff6000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7cfd000-b7d01000       Deferred        libdl.so.2
ELF     b7d01000-b7e4b000       Export          libc.so.6
ELF     b7e4c000-b7e64000       Export          libpthread.so.0
ELF     b7e6e000-b7f82000       Deferred        libwine.so.1
ELF     b7f84000-b7fa0000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
        0000001e    0
        0000001d    0
        0000001c   15
        0000001b    0
        00000009    0
0000000c 
        00000025    0
        00000020    0
        00000017    0
        00000016    0
        00000011    0
        00000010    0
        0000000e    0
        0000000d    0
00000012 
        00000015    0
        00000014    0
        00000013    0
00000018 
        0000001a    0
        00000019    0
00000021 (D) C:\windows\system32\winedevice.exe
        00000024    0 <==
        00000023    0
        00000022    0
Backtrace:
=>1 0x7b841042 RaiseException+0x7a() in kernel32 (0x7ecce8bc)
  2 0x7ee005dd in ntoskrnl (+0x105dd) (0x7ecce8dc)
  3 0x7edf8c38 in ntoskrnl (+0x8c38) (0x7ecce9c8)
  4 0x7ee50c0d in advapi32 (+0x30c0d) (0x7eccea18)
  5 0x7bc684c6 call_thread_entry_point+0xe() in ntdll (0x7eccea28)
  6 0x7bc6927d in ntdll (+0x5927d) (0x7eccead8)
  7 0x7bc69d24 NtQueueApcThread() in ntdll (0x7eccf3d8)
  8 0xb7e5146b start_thread+0xcb() in libpthread.so.0 (0x7eccf4c8)
  9 0xb7dd46de __clone+0x5e() in libc.so.6 (0x00000000)
wine: Call from 0x7b840fc8 to unimplemented function ntoskrnl.exe.IoGetDeviceAttachmentBaseRef, aborting
Deleting active MRSW lock (0x110dc4), expect failure
```

---

### Post by cogadh on 2008-06-10
Not really a lot. All of the "fixme" messages are just developer notes about unimplmented or incomplete functions in Wine. There is nothing you can do about them and most applications run with Wine will encounter a few of them, but still run fine. The bottom half of the error is just a register dump. Basically, Wine is puking because of what you fed it. Chances are, that dump was caused by this (the only actual error you got):
```
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\windows\\system32\\WzFlashRenderer.dll") not found
```
Basically, MapleStory is looking for a particular DLL file that does not exist in Wine, but probably exists in a normal Windows environment. All you need to do to fix that is copy the MSVCP71.dll file from a Windows machine (found in C:\windows\system32), place it in Wine's system32 directory (~/.wine/drive_c/windows/system32) then run winecfg and apply a library override for it. When you try running the game again, that error should go away, but new ones may crop up. If it does error out again, post the output again and hopefully I can decipher something else from it.

---

### Post by Takebacker on 2008-06-10
```
takebacker@takebacker-laptop:~$ wine OdinMS.exe
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
err:alsa:ALSA_CheckSetVolume Could not find 'PCM Playback Volume' element
fixme:mixer:ALSA_MixerInit No master control found on Intel ICH6 Modem, disabling mixer
fixme:win:EnumDisplayDevicesW ((null),0,0x33f3d0,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:imm:ImmGetDefaultIMEWnd (0x10026 - (nil) 0x132390 ): semi-stub
wine: Call from 0x7b840fc8 to unimplemented function msvcr71.dll.__iob_func, aborting
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100
fixme:wininet:FtpGetFileSize (0x3, (nil))
fixme:dsound:IDirectSoundBufferImpl_Restore (0x3f368068):stub
fixme:dsound:IDirectSoundBufferImpl_Restore (0x3f48eee8):stub
wine: Call from 0x7b840fc8 to unimplemented function ntoskrnl.exe.IoGetCurrentProcess, aborting
wine: Unimplemented function ntoskrnl.exe.IoGetCurrentProcess called at address 0x7b840fc8 (thread 0023), starting debugger...
Unhandled exception: unimplemented function ntoskrnl.exe.IoGetCurrentProcess called in 32-bit code (0x7b841042).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:7b841042 ESP:7ecc4858 EBP:7ecc48bc EFLAGS:00200212(   - 00      - -IA1)
 EAX:7b82c171 EBX:7b8ac8a0 ECX:00000000 EDX:7ecc48d4
 ESI:7ecc48d4 EDI:004500d0
Stack dump:
0x7ecc4858:  7ecc48d4 00000008 00450000 80000100
0x7ecc4868:  00000001 00000000 7b840fc8 00000002
0x7ecc4878:  7edf6640 7edf865c 00000128 7ecc48b0
0x7ecc4888:  7ecc48c8 7b842ae3 7ffd0bf8 7ecc48b0
0x7ecc4898:  7b862f14 7bc40be1 7ffd0c00 7ecc48b8
0x7ecc48a8:  00110014 7bc32fe9 7b840fd2 7ee71960
Backtrace:
=>1 0x7b841042 RaiseException+0x7a() in kernel32 (0x7ecc48bc)
  2 0x7edf65dd in ntoskrnl (+0x165dd) (0x7ecc48dc)
  3 0x7edeec38 in ntoskrnl (+0xec38) (0x7ecc49c8)
  4 0x7ee46c0d in advapi32 (+0x26c0d) (0x7ecc4a18)
  5 0x7bc684c6 call_thread_entry_point+0xe() in ntdll (0x7ecc4a28)
  6 0x7bc6927d in ntdll (+0x5927d) (0x7ecc4ad8)
  7 0x7bc69d24 NtQueueApcThread() in ntdll (0x7ecc53d8)
  8 0xb7e9a46b start_thread+0xcb() in libpthread.so.0 (0x7ecc54c8)
  9 0xb7e1d6de __clone+0x5e() in libc.so.6 (0x00000000)
0x7b841042 RaiseException+0x7a in kernel32: subl        $4,%esp
Modules:
Module  Address                 Debug info      Name (31 modules)
PE        450000-  455400       Deferred        npkcrypt.sys
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bca2000       Export          ntdll<elf>
  \-PE  7bc10000-7bca2000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7eaac000-7eac1000       Deferred        hal<elf>
  \-PE  7eab0000-7eac1000       \               hal
ELF     7eac1000-7eb26000       Deferred        msvcrt<elf>
  \-PE  7ead0000-7eb26000       \               msvcrt
ELF     7eb26000-7eb39000       Deferred        libresolv.so.2
ELF     7eb39000-7eb57000       Deferred        iphlpapi<elf>
  \-PE  7eb40000-7eb57000       \               iphlpapi
ELF     7eb57000-7ebb5000       Deferred        rpcrt4<elf>
  \-PE  7eb60000-7ebb5000       \               rpcrt4
ELF     7edd7000-7ee0f000       Export          ntoskrnl<elf>
  \-PE  7ede0000-7ee0f000       \               ntoskrnl
ELF     7ee0f000-7ee5e000       Export          advapi32<elf>
  \-PE  7ee20000-7ee5e000       \               advapi32
ELF     7ee5e000-7ee72000       Deferred        winedevice<elf>
  \-PE  7ee60000-7ee72000       \               winedevice
ELF     7ee72000-7ee7d000       Deferred        libnss_files.so.2
ELF     7ee7d000-7ee87000       Deferred        libnss_nis.so.2
ELF     7ee87000-7ee9f000       Deferred        libnsl.so.1
ELF     7ee9f000-7eea8000       Deferred        libnss_compat.so.2
ELF     7efd1000-7eff6000       Deferred        libm.so.6
ELF     b7d46000-b7d4a000       Deferred        libdl.so.2
ELF     b7d4a000-b7e94000       Export          libc.so.6
ELF     b7e95000-b7ead000       Export          libpthread.so.0
ELF     b7eb7000-b7fcb000       Deferred        libwine.so.1
ELF     b7fcd000-b7fe9000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 
        0000001d    0
        0000001c    0
        0000001b   15
        0000001a    0
        00000009    0
0000000c 
        00000024    0
        0000001f    0
        00000016    0
        00000015    0
        00000010    0
        0000000e    0
        0000000d    0
00000011 
        00000014    0
        00000013    0
        00000012    0
00000017 
        00000019    0
        00000018    0
00000020 (D) C:\windows\system32\winedevice.exe
        00000023    0 <==
        00000022    0
        00000021    0
Backtrace:
=>1 0x7b841042 RaiseException+0x7a() in kernel32 (0x7ecc48bc)
  2 0x7edf65dd in ntoskrnl (+0x165dd) (0x7ecc48dc)
  3 0x7edeec38 in ntoskrnl (+0xec38) (0x7ecc49c8)
  4 0x7ee46c0d in advapi32 (+0x26c0d) (0x7ecc4a18)
  5 0x7bc684c6 call_thread_entry_point+0xe() in ntdll (0x7ecc4a28)
  6 0x7bc6927d in ntdll (+0x5927d) (0x7ecc4ad8)
  7 0x7bc69d24 NtQueueApcThread() in ntdll (0x7ecc53d8)
  8 0xb7e9a46b start_thread+0xcb() in libpthread.so.0 (0x7ecc54c8)
  9 0xb7e1d6de __clone+0x5e() in libc.so.6 (0x00000000)
wine: Call from 0x7b840fc8 to unimplemented function ntoskrnl.exe.IoGetDeviceAttachmentBaseRef, aborting
wine: Call from 0x7b840fc8 to unimplemented function ntoskrnl.exe.IoGetDeviceInterfaceAlias, aborting
Deleting active MRSW lock (0x11179c), expect failure

```

Very frustrating indeed. I can only imagine how annoying it's going to be when i have to upgrade either wine or odin. =/

---

### Post by cogadh on 2008-06-11
Well, I was kind of hoping that getting that DLL would make those ntoskrnl.exe errors go away, but it looks like it didn't. Wine's implementation of ntoskrnl.exe is less than half complete, so it is relatively easy to find apps that will error on it. You can try replacing Wine's ntoskrnl.exe with a real one from Windows, but I've never actually had that work for me.

If Wine doesn't work, then you might want to consider using a virtual machine (VMWare, VirtualBox, etc.) to run it. The regular version of MapleStory was reported to work in this manner, Odin may work even better:
[http://ubuntuforums.org/showthread.php?t=372928](http://ubuntuforums.org/showthread.php?t=372928)

---

