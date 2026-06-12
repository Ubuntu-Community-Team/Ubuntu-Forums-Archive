---
title: "Error for Spore Creature Creator (12.04 Ubuntu)"
date: 2012-12-09
forum: Wine
---

### Post by Dudemister1999 on 2012-12-09
Good day, ladies and gentlemen. I come to you once more with an error, in the hopes it can be resolved. Today's error comes from SPORE(TM) Creature Creator. I am using WINE 1.4, and here is the error, starting from me running the game:

```
alex@alex-Satellite-L305:~/.wine/dosdevices/c:/Program Files/Electronic Arts/SPORE/Sporebin$ wine SporeCreatureCreator.exe -safe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
err:rpc:I_RpcGetBuffer no binding
fixme:win:EnumDisplayDevicesW ((null),0,0x2069044,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x2068bc4,0x00000000), stub!
fixme:file:K32EnumPageFilesA (0x14cb840, 0x2049b3c) stub
fixme:file:K32EnumPageFilesA (0x14cb840, 0x2014458) stub
fixme:win:EnumDisplayDevicesW ((null),0,0x1fb06dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x1fb025c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x1fb0568,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x1fb00e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x1fb0568,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x1fb00e8,0x00000000), stub!
err:listview:LISTVIEW_WindowProc unknown msg 108a wp=00000000 lp=0204f528
fixme:win:EnumDisplayDevicesW ((null),0,0x1fafb64,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x1faf6e4,0x00000000), stub!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:win:EnumDisplayDevicesW ((null),0,0x1fb03ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x1faff6c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x1fb99ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x1fb956c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x1fb06e0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x1fb0260,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x1fb8858,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x1fb83d8,0x00000000), stub!
fixme:process:GetLogicalProcessorInformation ((nil),0x2065978): stub
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
err:rpc:I_RpcGetBuffer no binding
fixme:thread:SetThreadIdealProcessor (0x7a8): stub
fixme:thread:SetThreadIdealProcessor (0x7b0): stub
fixme:system:SystemParametersInfoW Unimplemented action: 94 (SPI_GETMOUSETRAILS)
fixme:system:SystemParametersInfoW Unimplemented action: 4124 (SPI_GETMOUSESONAR)
fixme:win:EnumDisplayDevicesW ((null),0,0x207ee24,0x00000000), stub!
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:thread:SetThreadIdealProcessor (0x824): stub
fixme:thread:SetThreadIdealProcessor (0x87c): stub
fixme:thread:SetThreadIdealProcessor (0x894): stub
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
err:ntdll:RtlpWaitForCriticalSection section 0x769c1c0 "?" wait timed out in thread 002e, blocked by 002c, retrying (60 sec)
^[^[^[^[^[^[^[fixme:dbghelp:elf_search_auxv can't find symbol in module
err:mmtime:TIME_MMTimeStop Timer still active?!
```


Thank you for your time, and have a wonderful evening. ):P

-Alex

---

### Post by Dudemister1999 on 2012-12-17
Can no one help? This game is just taking space out of my hard drive till it gets resolved. :confused:

---

