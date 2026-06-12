---
title: "Borderlands install help"
date: 2012-07-29
forum: Wine
---

### Post by Ognido on 2012-07-29
I've been trying to get Borderlands installed for several months now and have just decided to put out my problems to everyone to see if they have any suggestions. I am *_[COLOR=Black]trying[/COLOR]_* to run in Ubuntu 12.04 32 bit, Wine version 1.5.9, using winetricks to install all required programs before hand.

Hardware:
Intel® Core™2 Quad CPU Q9300 @ 2.50GHz
4GB
Power Color Radeon HD 6870 with 1 GB

 Here is the output of  wine setup.exe:

[SIZE=2]******@Beast:/media/Borderlands$ wine Setup.exe
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:vbscript:p****_script parser failed on parsing L"      Property(\"WiseNextDialog\") = NextDialog\r\n      if (Property(\"WiseDialogStack\") <> \"\") Then\r\n         Property(\"WiseDialogStack\") = Property(\"WiseDialogStack\") & \"|\" & CurrDialog\r\n      else\r\n         Property(\"WiseDialogStack\") = Property(\"WiseDialogStack\") & CurrDialog\r"...
err:msi:msi_dialog_create_controls no handler for element type L"Billboard"
fixme:clusapi:GetNodeClusterState ((null),0x33ec04) stub!
fixme:advapi:DecryptFileA "h:\\ec4d56aa3fbc79d6660ca5ac23\\" 00000000
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:LsaOpenPolicy ((null),0x33f304,0x00000001,0x33f32c) stub
fixme:advapi:LsaClose (0xcafe) stub
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:storage:create_storagefile Storage share mode not implemented.
err:msi:ITERATE_Actions Execution halted, action L"NO_AUTO_DOWNGRADE" returned 1603
fixme:setupapi:CMP_WaitNoPendingInstallEvents 100
fixme:setupapi:pSetupGetGlobalFlags stub
fixme:wintrust:WinVerifyTrust unimplemented for 3
fixme:ntdll:server_ioctl_file Unsupported ioctl 9c040 (device=9 access=3 func=10 method=0)
fixme:setupapi:pSetupGetGlobalFlags stub
fixme:setupapi:pSetupGetGlobalFlags stub
fixme:wintrust:WinVerifyTrust unimplemented for 3
fixme:setupapi:pSetupGetGlobalFlags stub
fixme:shell:SHChangeNotify ignoring unsupported flags: 2001
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:setupapi:do_file_copyW Unsupported style(s) 0x144
err:msi:extract_cabinet FDICopy failed
err:msi:ACTION_InstallFiles Failed to extract cabinet: L"Setup3.cab"
err:msi:ITERATE_Actions Execution halted, action L"InstallFiles" returned 1603
err:msi:ITERATE_Actions Execution halted, action L"ExecuteAction" returned 1603
err:msi:ITERATE_RemoveFolders Unable to resolve folder L"INSTALLDIR7"[/SIZE]



I have tried numerous walk-through and help files on line and AppDB. Any help would be GREATLY appreciated!!!!

Let me know if you need any more info.

---

### Post by madjr on 2012-07-29
hmm seems it doesnt want to finish the installation ?

---

### Post by Ognido on 2012-07-29
Yeah, it seems to go through a good part of it, then it just stops. It sits at the initializing screen the whole time in the gui though...

---

### Post by madjr on 2012-07-29
> **Ognido said:**
> Yeah, it seems to go through a good part of it, then it just stops. It sits at the initializing screen the whole time in the gui though...

are you installing from a downloaded executable or from physical media like a DvD ?

---

### Post by Ognido on 2012-07-30
It is a DVD.

---

### Post by madjr on 2012-07-30
> **Ognido said:**
> It is a DVD.

hmm, It might be corrupted... has happened to me a lot of times. :(

can you copy the contents into your hard drive (also check you have enough space on your linux partition for the installation) or have tried to install it lately in windows ?

---

### Post by Ognido on 2012-07-30
> **madjr said:**
> hmm, It might be corrupted... has happened to me a lot of times. :(

can you copy the contents into your hard drive (also check you have enough space on your linux partition for the installation) or have tried to install it lately in windows ?


It is a retail dvd.  When trying to copy the files I get "Error splicing file: Input/output error" on some of the cab files.  They are on Cabs 3,4,5,7. If anyone has these cab files, I'd greatly appreciate copies. I assume my DVD has gotten scratched.

---

### Post by Ognido on 2012-07-30
I have cleaned the DVD and the cab files copied correctly, trying to install now. Will post with update.

---

### Post by madjr on 2012-07-30
> **Ognido said:**
> It is a retail dvd.  When trying to copy the files I get "Error splicing file: Input/output error" on some of the cab files.  They are on Cabs 3,4,5,7. If anyone has these cab files, I'd greatly appreciate copies. I assume my DVD has gotten scratched.

yep as seen on the text you pasted in the first post.

```
err:msi:ACTION_InstallFiles Failed to extract cabinet: L"Setup3.cab"
```

anyway fingers crossed :D

---

### Post by Ognido on 2012-07-30
Here is what I get now:

*****@Beast:~/.wine/drive_c/Program Files/2K Games/Gearbox Software/Borderlands/Binaries$ wine Borderlands.exe
err:module:find_forwarded_export function not found for forward 'msvcrt.__CxxFrameHandler3' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt.fopen_s' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt.strcpy_s' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt.strncpy_s' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt._initterm_e' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt.__CppXcptFilter' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt._vsnprintf_s' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt._except_handler4_common' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt.__CppXcptFilter' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt._except_handler4_common' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt._initterm_e' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt._aligned_realloc' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt._aligned_malloc' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt._aligned_free' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt.strcpy_s' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt.strcat_s' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt._aligned_realloc' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt._initterm_e' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt.__CppXcptFilter' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt._except_handler4_common' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt._aligned_malloc' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt._aligned_free' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt._except_handler4_common' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt.__CppXcptFilter' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt._initterm_e' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt._aligned_malloc' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt._except_handler4_common' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt.__CppXcptFilter' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt._initterm_e' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt._aligned_free' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt._aligned_malloc' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
err:module:find_forwarded_export function not found for forward 'msvcrt._aligned_realloc' used by L"C:\\windows\\system32\\msvcr80.dll". If you are using builtin L"msvcr80.dll", try using the native one instead.
wine: Call from 0x7bc4a130 to unimplemented function msvcrt.dll._set_printf_count_output, aborting
err:module:attach_process_dlls "msvcr80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\2K Games\\Gearbox Software\\Borderlands\\Binaries\\Borderlands.exe" failed, status 80000100


I went into wine config, there was no msvcr80.dll, but I do have msvcr90.dll. It is located where it's looking for it though... It is set to Native then builtin.

BTW, I appreciate the time you're spending to help me.

---

### Post by Ognido on 2012-07-30
I found the file and installed it through winetricks. I now get the splash screnn then the window resizes and nothing comes up. Here's what the console gives me:


[email]nathan@Beast:~/.wine[/email]/drive_c/Program Files/2K Games/Gearbox Software/Borderlands/Binaries$ wine Borderlands.exe
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
err:rpc:I_RpcGetBuffer no binding
fixme:win:EnumDisplayDevicesW ((null),0,0x34dab44,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34da6c4,0x00000000), stub!
fixme:file:K32EnumPageFilesA (0x2616d10, 0x34b9730) stub
fixme:file:K32EnumPageFilesA (0x2616d10, 0x348404c) stub
fixme:win:EnumDisplayDevicesW ((null),0,0x341e2a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x341de28,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x341e2ac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x341de2c,0x00000000), stub!
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQuerySystemInformation (0x00000007,0x34b0fb0,0x00000018,(nil)) stub
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 2d0c04 (device=2d access=0 func=301 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 2d0c04 (device=2d access=0 func=301 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:cdrom:CDROM_GetMediaType : faking success
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 41018 (device=4 access=0 func=406 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 41018 (device=4 access=0 func=406 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 2d4800 (device=2d access=1 func=200 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 2d4800 (device=2d access=1 func=200 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 2d0800 (device=2d access=0 func=200 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 2d0800 (device=2d access=0 func=200 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 2d0c04 (device=2d access=0 func=301 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 2d0c04 (device=2d access=0 func=301 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d014 (device=4 access=3 func=405 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d014 (device=4 access=3 func=405 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d014 (device=4 access=3 func=405 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d014 (device=4 access=3 func=405 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d014 (device=4 access=3 func=405 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d014 (device=4 access=3 func=405 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d0000 (device=4d access=0 func=0 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d0000 (device=4d access=0 func=0 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d014 (device=4 access=3 func=405 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d014 (device=4 access=3 func=405 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 24058 (device=2 access=1 func=16 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 24058 (device=2 access=1 func=16 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 24058 (device=2 access=1 func=16 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 24058 (device=2 access=1 func=16 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d014 (device=4 access=3 func=405 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d014 (device=4 access=3 func=405 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d014 (device=4 access=3 func=405 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d014 (device=4 access=3 func=405 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d014 (device=4 access=3 func=405 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 4d014 (device=4 access=3 func=405 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 2404c (device=2 access=1 func=13 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 2404c (device=2 access=1 func=13 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 2d4804 (device=2d access=1 func=201 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 2d4804 (device=2d access=1 func=201 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 4d0000 (device=4d access=0 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 4d0000 (device=4d access=0 func=0 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24058 (device=2 access=1 func=16 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24058 (device=2 access=1 func=16 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24058 (device=2 access=1 func=16 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 24058 (device=2 access=1 func=16 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 4d0008 (device=4d access=0 func=2 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:cursor:SetSystemCursor (0x10054,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1007e,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1008c,00007f03),stub!
fixme:cursor:SetSystemCursor (0x1009a,00007f01),stub!
fixme:cursor:SetSystemCursor (0x100a8,00007f88),stub!
fixme:cursor:SetSystemCursor (0x100b6,00007f86),stub!
fixme:cursor:SetSystemCursor (0x100c4,00007f83),stub!
fixme:cursor:SetSystemCursor (0x100d2,00007f82),stub!
fixme:cursor:SetSystemCursor (0x100e0,00007f84),stub!
fixme:cursor:SetSystemCursor (0x100ee,00007f04),stub!
fixme:cursor:SetSystemCursor (0x100fc,00007f02),stub!
fixme:cursor:SetSystemCursor (0x10054,00007f00),stub!
fixme:cursor:SetSystemCursor (0x8002a,00007f00),stub!
fixme:cursor:SetSystemCursor (0x80020,00007f03),stub!
fixme:cursor:SetSystemCursor (0x20028,00007f01),stub!
fixme:cursor:SetSystemCursor (0x20024,00007f88),stub!
fixme:cursor:SetSystemCursor (0x20064,00007f86),stub!
fixme:cursor:SetSystemCursor (0x10068,00007f83),stub!
fixme:cursor:SetSystemCursor (0x1006c,00007f85),stub!
fixme:cursor:SetSystemCursor (0x10070,00007f82),stub!
fixme:cursor:SetSystemCursor (0x10074,00007f84),stub!
fixme:cursor:SetSystemCursor (0x10078,00007f04),stub!
fixme:cursor:SetSystemCursor (0x1007c,00007f02),stub!
fixme:process:GetLogicalProcessorInformation ((nil),0x34d7498): stub
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
err:rpc:I_RpcGetBuffer no binding
fixme:heap:HeapSetInformation 0x40c4000 0 0x34ef69c 4
fixme:gameux:GameExplorerImpl_VerifyAccess (0x1458c8, L"C:\\Program Files\\2K Games\\Gearbox Software\\Borderlands\\Binaries\\Borderlands.exe", 0x34eee4c)
fixme:win:EnumDisplayDevicesW ((null),0,0x34edb20,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34eefd4,0x00000000), stub!
fixme:winediag:AUDDRV_GetAudioEndpoint Winepulse is not officially supported by the wine project
fixme:winediag:AUDDRV_GetAudioEndpoint For sound related feedback and support, please visit [http://ubuntuforums.org/showthread.php?t=1960599](http://ubuntuforums.org/showthread.php?t=1960599)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)
fixme:d3d:debug_d3dformat Unrecognized 0x34324644 (as fourcc: DF24) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x34324644) in the format lookup table
err:d3d:context_create wglSwapIntervalEXT failed to set swap interval 0 for context 0x1c3408, last error 0x591
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
err:d3d:context_create wglSwapIntervalEXT failed to set swap interval 0 for context 0x2ee2bb08, last error 0x591
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1565
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1565
err:d3d:state_pscale >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glPointSize(...); @ state.c / 1565
fixme:imm:ImmReleaseContext (0x1010e, 0x1df090): stub



If I understand this, I'm having an issue with DirectX...?

---

### Post by madjr on 2012-07-30
am sure you followed most of what is here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=18686&iTestingId=47494](http://appdb.winehq.org/objectManager.php?sClass=version&iId=18686&iTestingId=47494)

but, is usually hard to know if the game was really successfully installed and works (even if it seemed to have finished.)

What I usually do is install a game in windows make sure it works and then If I want I can copy the installed folder to linux (sometimes with a no cd/dvd patch) to make a backup copy (in case the dvd gets corrupted).

that way is so much easier to know if its the game that is failing or something else.

---

### Post by Ognido on 2012-07-31
> **madjr said:**
> am sure you followed most of what is here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=18686&iTestingId=47494](http://appdb.winehq.org/objectManager.php?sClass=version&iId=18686&iTestingId=47494)

I could not find the page as I was using the DVD version and went to the 1.4 patch. Thanks for showing it to me. I started over with a new wine prefix, following the instructions. I now get this in console.

*****@Beast:~$ WINEPREFIX=~/.wine/borderlands wine Borderlands.exe
err:module:import_dll Library wxmsw28u_core_vc_custom.dll (which is needed by L"C:\\windows\\system32\\Borderlands.exe") not found
err:module:import_dll Library wxmsw28u_aui_vc_custom.dll (which is needed by L"C:\\windows\\system32\\Borderlands.exe") not found
err:module:import_dll Library wxmsw28u_xrc_vc_custom.dll (which is needed by L"C:\\windows\\system32\\Borderlands.exe") not found
err:module:import_dll Library wxmsw28u_richtext_vc_custom.dll (which is needed by L"C:\\windows\\system32\\Borderlands.exe") not found
err:module:import_dll Library wxmsw28u_html_vc_custom.dll (which is needed by L"C:\\windows\\system32\\Borderlands.exe") not found
err:module:import_dll Library wxmsw28u_adv_vc_custom.dll (which is needed by L"C:\\windows\\system32\\Borderlands.exe") not found
err:module:import_dll Library wxmsw28u_vc_custom.dll (which is needed by L"C:\\windows\\system32\\Borderlands.exe") not found
err:module:import_dll Library nvtt.dll (which is needed by L"C:\\windows\\system32\\Borderlands.exe") not found
err:module:import_dll Library vorbis.dll (which is needed by L"C:\\windows\\system32\\Borderlands.exe") not found
err:module:import_dll Library vorbisenc.dll (which is needed by L"C:\\windows\\system32\\Borderlands.exe") not found
err:module:import_dll Library vorbisfile.dll (which is needed by L"C:\\windows\\system32\\Borderlands.exe") not found
err:module:import_dll Library ogg.dll (which is needed by L"C:\\windows\\system32\\Borderlands.exe") not found
err:module:import_dll Library fmodex.dll (which is needed by L"C:\\windows\\system32\\Borderlands.exe") not found
err:module:import_dll Library binkw32.dll (which is needed by L"C:\\windows\\system32\\Borderlands.exe") not found
err:module:import_dll Library PhysXExtensions.dll (which is needed by L"C:\\windows\\system32\\Borderlands.exe") not found
err:module:import_dll Library libresample.dll (which is needed by L"C:\\windows\\system32\\Borderlands.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\Borderlands.exe" failed, status c0000135


  Any suggestions?

---

### Post by madjr on 2012-07-31
seems to be looking for this path:

```
C:\\windows\\system32\\
```

did you copy over from windows or is the same one you installed under linux ?

---

### Post by Ognido on 2012-07-31
It's the same one in Linux. I've got a netbook running XP, tinking about installing Borderlands on it. How do I copy it over to Ubuntu? Put all the files on a USB stick, move them over to a wine prefix?

---

### Post by madjr on 2012-08-01
> **Ognido said:**
> It's the same one in Linux. I've got a netbook running XP, tinking about installing Borderlands on it. How do I copy it over to Ubuntu? Put all the files on a USB stick, move them over to a wine prefix?

yes, good idea.

once you install and confirm is working correctly, it may be possible just to copy it without much problem.

But the important thing here is just to know the game still works as expected in windows because if it doesnt then no point trying to get it to work on wine. So fingers crossed!

---

