---
title: "Problem with launching Crysis via Wine"
date: 2014-06-24
forum: Wine
---

### Post by jacob40 on 2014-06-24
I'm a new member of this forum, so- Hello : )
I installed Crysis today on Ubuntu 12.04 (32 b) and I did it. Everything went quite fine. Then, I wanted to launch it. 
Tried to launch with Wine 1.6.1 in GUI - nothing happened (there was a process running named Crysis.exe using some processing power, and then it died). Then I launched it by terminal and I got this code:

[email]sowith@sowith-MS-7695:~/.wine[/email]/drive_c/Program Files/Electronic Arts/Crytek/Crysis/Bin32$ wine Crysis.exe
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
err:rpc:I_RpcGetBuffer no binding
fixme:win:EnumDisplayDevicesW ((null),0,0x5190e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x518c68,0x00000000), stub!
fixme:file:K32EnumPageFilesA (0x374081e0, 0x4f9c70) stub
fixme:file:K32EnumPageFilesA (0x374081e0, 0x4c458c) stub
fixme:win:EnumDisplayDevicesW ((null),0,0x465798,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x465318,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x465798,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x465318,0x00000000), stub!
fixme:cdrom:CDROM_GetMediaType : faking success
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
fixme:ntdll:NtQuerySystemInformation (0x00000007,0x4f1edc,0x00000018,(nil)) stub
fixme:ntdll:server_ioctl_file Unsupported ioctl 4d0008 (device=4d access=0 func=2 method=0)
fixme:cursor:SetSystemCursor (0x80322,00007f00),stub!
fixme:cursor:SetSystemCursor (0x302e4,00007f00),stub!
fixme:cursor:SetSystemCursor (0x302d6,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x302c8,00007f03),stub!
fixme:cursor:SetSystemCursor (0x302ba,00007f01),stub!
fixme:cursor:SetSystemCursor (0x302ac,00007f88),stub!
fixme:cursor:SetSystemCursor (0x3029e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x30290,00007f83),stub!
fixme:cursor:SetSystemCursor (0x30282,00007f82),stub!
fixme:cursor:SetSystemCursor (0x80260,00007f84),stub!
fixme:cursor:SetSystemCursor (0x9024e,00007f04),stub!
fixme:cursor:SetSystemCursor (0xd0240,00007f02),stub!
fixme:cursor:SetSystemCursor (0x80322,00007f00),stub!
fixme:cursor:SetSystemCursor (0x9030e,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x9030c,00007f00),stub!
fixme:cursor:SetSystemCursor (0x30308,00007f03),stub!
fixme:cursor:SetSystemCursor (0x30306,00007f01),stub!
fixme:cursor:SetSystemCursor (0x30302,00007f88),stub!
fixme:cursor:SetSystemCursor (0x302fe,00007f86),stub!
fixme:cursor:SetSystemCursor (0x302fa,00007f83),stub!
fixme:cursor:SetSystemCursor (0x302f6,00007f85),stub!
fixme:cursor:SetSystemCursor (0x302f2,00007f82),stub!
fixme:cursor:SetSystemCursor (0x302ee,00007f84),stub!
fixme:cursor:SetSystemCursor (0x302ea,00007f04),stub!
fixme:cursor:SetSystemCursor (0x302e6,00007f02),stub!
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
err:rpc:I_RpcGetBuffer no binding
fixme:win:EnumDisplayDevicesW ((null),0,0x52e418,0x00000000), stub!
fixme:dxgi:dxgi_device_init Ignoring adapter type.
err:module:find_forwarded_export module not found for forward 'msvcp90.??1?$basic_string@DU?$char_traits@D@std@@V?$allocator@D@2@@std@@QAE@XZ' used by L"C:\\windows\\system32\\msvcp80.dll"
err:module:find_forwarded_export module not found for forward 'msvcp90.??0?$basic_string@DU?$char_traits@D@std@@V?$allocator@D@2@@std@@QAE@PBD@Z' used by L"C:\\windows\\system32\\msvcp80.dll"
err:module:find_forwarded_export module not found for forward 'msvcp90.??0?$basic_string@DU?$char_traits@D@std@@V?$allocator@D@2@@std@@QAE@ABV01@@Z' used by L"C:\\windows\\system32\\msvcp80.dll"
fixme:msvcrt:__clean_type_info_names_internal (0x3405ccc0) stub
fixme:msvcrt:__clean_type_info_names_internal (0x3540fb84) stub
fixme:msvcrt:__clean_type_info_names_internal (0x395d7228) stub
fixme:msvcrt:__clean_type_info_names_internal (0x307dd598) stub
fixme:msvcrt:__clean_type_info_names_internal (0x36709f10) stub
fixme:msvcrt:__clean_type_info_names_internal (0x392a93c8) stub


I really don't understand it, that's why i'm here. If anybody does understand it or has met something similar please leave a responce. 
Sorry for mistakes and bad English ^^,

---

### Post by Mark Phelps on 2014-06-24
Don't know what version you're trying to run, but the Wine ratings are all over the chart: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=5880]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=5880")

---

