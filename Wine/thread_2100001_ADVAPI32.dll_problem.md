---
title: "ADVAPI32.dll problem?"
date: 2012-12-31
forum: Wine
---

### Post by gimchicoffee on 2012-12-31
Hi, I have been playing steam games just fine for months now. one of my favourites, empires mod, did a version update and i can no longer play it. in terminal it says 


ixme:win:EnumDisplayDevicesW ((null),0,0x33cf84,0x00000000), stub!
fixme:appbar:SHAppBarMessage unknown msg: 4
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=3): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=1): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=0): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=2): stub
fixme:dwmapi:DwmSetWindowAttribute (0x1012c, 2, 0x33d4f0, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x1012c, 3, 0x33d4fc, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x1012c, 4, 0x33d4ec, 4) stub
wine: Install Mono for Windows to run .NET 2.0 applications.
wine: Call from 0x7bc49e20 to unimplemented function ADVAPI32.dll.StopTraceA, aborting
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100
wine: Call from 0x7bc49e20 to unimplemented function ADVAPI32.dll.StopTraceA, aborting
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100
wine: Call from 0x7bc49e20 to unimplemented function ADVAPI32.dll.StopTraceA, aborting
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100
wine: Call from 0x7bc49e20 to unimplemented function ADVAPI32.dll.StopTraceA, aborting
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100
^Cfixme:console:CONSOLE_DefaultHandler Terminating process 8 on event 0
err:ntdll:RtlpWaitForCriticalSection section 0x7bcb08e4 "loader.c: loader_section" wait timed out in thread 0027, blocked by 0055, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7bcb08e4 "loader.c: loader_section" wait timed out in thread 0009, blocked by 0055, retrying (60 sec)





-i tried installing mono for NET 2.0 or whatever but it didnt seem to work. i installed 2.1.0 using winetricks

please help anyone

---

### Post by dino99 on 2012-12-31
is the database help ?

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1163](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1163)

[http://wiki.winehq.org/Mono](http://wiki.winehq.org/Mono)

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3754](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3754)

note: the "fixme" are only warnings, not errors (kind of todo for devs)
note2: you might install dotnet2 (.net) but not mono (as they dont play nicely together). So start with a fresh new .wine (simply rename the actual to .wine-orig or so)
note3: use the latest wine from ppa   [https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

---

### Post by Toz on 2012-12-31
See: [http://bugs.winehq.org/show_bug.cgi?id=31861]("http://bugs.winehq.org/show_bug.cgi?id=31861").

What version of wine are you running?

---

### Post by gimchicoffee on 2013-01-02
hmm, thanks. i tried updating to 1.5.2 but it still doesnt load. now it says


[B]fixme:advapieregisterEventSource (0xcafe4242) stub
wine: Call from 0x7bc49f80 to unimplemented function ADVAPI32.dll.StopTraceA, aborting
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100
wine: Call from 0x7bc49f80 to unimplemented function ADVAPI32.dll.StopTraceA, aborting
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixmeprocess:GetLogicalProcessorInformation ((nil),0x33fd90): stub
fixmeprocess:GetLogicalProcessorInformation (0x4f3c48,0x33fd90): stub
err:service:service_send_start_message service L"Steam Client Service" failed to start
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixmerocess:GetLogicalProcessorInformation ((nil),0x33fd90): stub
fixmerocess:GetLogicalProcessorInformation (0x4f3c48,0x33fd90): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixmerocess:GetLogicalProcessorInformation ((nil),0x33fd90): stub
fixmerocess:GetLogicalProcessorInformation (0x4f3c48,0x33fd90): stub
err:service:service_send_start_message service L"Steam Client Service" failed to start
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixmerocess:GetLogicalProcessorInformation ((nil),0x33fd90): stub
fixmerocess:GetLogicalProcessorInformation (0x4f3c48,0x33fd90): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixmerocess:GetLogicalProcessorInformation ((nil),0x33fd90): stub
fixmerocess:GetLogicalProcessorInformation (0x4f3c48,0x33fd90): stub
fixme:advapi:RegisterEventSourceA ((null),"Steam Client Service"): stub
fixme:advapi:RegisterEventSourceW (L"",L"Steam Client Service"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0002,0x0000,0x80000002,(nil),0x0001,0x00000000,0x33f820,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0002,0x0000,0x80000002,(nil),0x0001,0x00000000,0x1305c0,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceA ((null),"Steam Client Service"): stub
fixme:advapi:RegisterEventSourceW (L"",L"Steam Client Service"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0xc0000001,(nil),0x0001,0x00000000,0x33f848,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0xc0000001,(nil),0x0001,0x00000000,0x132b90,(nil)): stub
err:eventlog:ReportEventW L"Failed to copy new service file to temp location"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\SOFTWARE\\Valve\\Steam" 4 4 (nil) (nil) 0x133558 (nil)
fixme:advapi:EventRegister {47a9201e-73b0-42ce-9821-7e134361bc6f}, 0x3f005800, 0x3f036b20, 0x3f036b18
fixme:advapi:EventRegister {58a9201e-73b0-42ce-9821-7e134361bc70}, 0x3f005800, 0x3f036b58, 0x3f036b50
fixme:advapi:EventRegister {3fa9201e-73b0-43fe-9821-7e145359bc6f}, 0x3f005800, 0x3f036ae8, 0x3f036ae0
fixme:advapi:EventRegister {1432afee-73b0-42ce-9821-7e134361b433}, 0x3f005800, 0x3f036b90, 0x3f036b88
fixme:advapi:EventRegister {4372afee-73b0-42ce-9821-7e134361b519}, 0x3f005800, 0x3f036bc8, 0x3f036bc0
fixme:process:GetLogicalProcessorInformation ((nil),0x80e490): stub
fixme:process:GetLogicalProcessorInformation (0x810418,0x80e490): stub
wine: Call from 0x7bc49f80 to unimplemented function ADVAPI32.dll.StopTraceA, aborting
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100
fixme:advapi:RegisterEventSourceA ((null),"Steam Client Service"): stub
fixme:advapi:RegisterEventSourceW (L"",L"Steam Client Service"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0xc0000001,(nil),0x0001,0x00000000,0x80e778,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0xc0000001,(nil),0x0001,0x00000000,0x1333b8,(nil)): stub
err:eventlog:ReportEventW L"Failed to load Steam Service library."
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
[/B]

---

### Post by Toz on 2013-01-02
> hmm, thanks. i tried updating to 1.5.2 but it still doesnt load. now it says
According to the bug report, its been fixed in **1.5.15**

It also seems to be related to wine Windows Version being set to Vista or Win7. What do you have it set to?

---

### Post by gimchicoffee on 2013-01-06
sorry, still not working... :(

so im running ubuntu 11.10 and wine 1.5.2, i've tried setting it to win 7, XP and 2008. the output in terminal that I get for 2008 is below.

Other games on steam run fine, and this one used to before the update.

Should I try to install a dot net DLL instead of mono?


[PHP]

wine: Install Mono for Windows to run .NET 2.0 applications.
wine: Call from 0x7bc49f80 to unimplemented function ADVAPI32.dll.StopTraceA, aborting
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100
wine: Call from 0x7bc49f80 to unimplemented function ADVAPI32.dll.StopTraceA, aborting
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:process:GetLogicalProcessorInformation ((nil),0x33fd90): stub
fixme:process:GetLogicalProcessorInformation (0x4f3c48,0x33fd90): stub
err:service:service_send_start_message service L"Steam Client Service" failed to start
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:process:GetLogicalProcessorInformation ((nil),0x33fd90): stub
fixme:process:GetLogicalProcessorInformation (0x4f3c48,0x33fd90): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:process:GetLogicalProcessorInformation ((nil),0x33fd90): stub
fixme:process:GetLogicalProcessorInformation (0x4f3c48,0x33fd90): stub
err:service:service_send_start_message service L"Steam Client Service" failed to start
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:process:GetLogicalProcessorInformation ((nil),0x33fd90): stub
fixme:process:GetLogicalProcessorInformation (0x4f3c48,0x33fd90): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:process:GetLogicalProcessorInformation ((nil),0x33fd90): stub
fixme:process:GetLogicalProcessorInformation (0x4f3c48,0x33fd90): stub
fixme:advapi:RegisterEventSourceA ((null),"Steam Client Service"): stub
fixme:advapi:RegisterEventSourceW (L"",L"Steam Client Service"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0002,0x0000,0x80000002,(nil),0x0001,0x00000000,0x33f820,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0002,0x0000,0x80000002,(nil),0x0001,0x00000000,0x1305c0,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceA ((null),"Steam Client Service"): stub
fixme:advapi:RegisterEventSourceW (L"",L"Steam Client Service"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0xc0000001,(nil),0x0001,0x00000000,0x33f848,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0xc0000001,(nil),0x0001,0x00000000,0x132b90,(nil)): stub
err:eventlog:ReportEventW L"Failed to copy new service file to temp location"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\SOFTWARE\\Valve\\Steam" 4 4 (nil) (nil) 0x133570 (nil)
fixme:advapi:EventRegister {47a9201e-73b0-42ce-9821-7e134361bc6f}, 0x3f005800, 0x3f036b20, 0x3f036b18
fixme:advapi:EventRegister {58a9201e-73b0-42ce-9821-7e134361bc70}, 0x3f005800, 0x3f036b58, 0x3f036b50
fixme:advapi:EventRegister {3fa9201e-73b0-43fe-9821-7e145359bc6f}, 0x3f005800, 0x3f036ae8, 0x3f036ae0
fixme:advapi:EventRegister {1432afee-73b0-42ce-9821-7e134361b433}, 0x3f005800, 0x3f036b90, 0x3f036b88
fixme:advapi:EventRegister {4372afee-73b0-42ce-9821-7e134361b519}, 0x3f005800, 0x3f036bc8, 0x3f036bc0
fixme:process:GetLogicalProcessorInformation ((nil),0x80e490): stub
fixme:process:GetLogicalProcessorInformation (0x810418,0x80e490): stub
wine: Call from 0x7bc49f80 to unimplemented function ADVAPI32.dll.StopTraceA, aborting
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100
fixme:advapi:RegisterEventSourceA ((null),"Steam Client Service"): stub
fixme:advapi:RegisterEventSourceW (L"",L"Steam Client Service"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0xc0000001,(nil),0x0001,0x00000000,0x80e778,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0xc0000001,(nil),0x0001,0x00000000,0x132c68,(nil)): stub
err:eventlog:ReportEventW L"Failed to load Steam Service library."
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
wine: Call from 0x7bc49f80 to unimplemented function ADVAPI32.dll.StopTraceA, aborting
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100
wine: Call from 0x7bc49f80 to unimplemented function ADVAPI32.dll.StopTraceA, aborting
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100
fixme:advapi:RegisterEventSourceA ((null),"Steam Client Service"): stub
fixme:advapi:RegisterEventSourceW (L"",L"Steam Client Service"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0002,0x0000,0x80000002,(nil),0x0001,0x00000000,0x33f820,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0002,0x0000,0x80000002,(nil),0x0001,0x00000000,0x1305c0,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:process:GetLogicalProcessorInformation ((nil),0x33fd90): stub
fixme:process:GetLogicalProcessorInformation (0x4f3c48,0x33fd90): stub
err:service:service_send_start_message service L"Steam Client Service" failed to start
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:process:GetLogicalProcessorInformation ((nil),0x33fd90): stub
fixme:process:GetLogicalProcessorInformation (0x4f3c48,0x33fd90): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:process:GetLogicalProcessorInformation ((nil),0x33fd90): stub
fixme:process:GetLogicalProcessorInformation (0x4f3c48,0x33fd90): stub
err:service:service_send_start_message service L"Steam Client Service" failed to start
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:process:GetLogicalProcessorInformation ((nil),0x33fd90): stub
fixme:process:GetLogicalProcessorInformation (0x4f3c48,0x33fd90): stub
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:process:GetLogicalProcessorInformation ((nil),0x33fd90): stub
fixme:process:GetLogicalProcessorInformation (0x4f3c48,0x33fd90): stub
fixme:advapi:RegisterEventSourceA ((null),"Steam Client Service"): stub
fixme:advapi:RegisterEventSourceW (L"",L"Steam Client Service"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0002,0x0000,0x80000002,(nil),0x0001,0x00000000,0x33f820,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0002,0x0000,0x80000002,(nil),0x0001,0x00000000,0x1305c0,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceA ((null),"Steam Client Service"): stub
fixme:advapi:RegisterEventSourceW (L"",L"Steam Client Service"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0xc0000001,(nil),0x0001,0x00000000,0x33f848,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0xc0000001,(nil),0x0001,0x00000000,0x132b90,(nil)): stub
err:eventlog:ReportEventW L"Failed to copy new service file to temp location"
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\SOFTWARE\\Valve\\Steam" 4 4 (nil) (nil) 0x133570 (nil)
fixme:advapi:EventRegister {47a9201e-73b0-42ce-9821-7e134361bc6f}, 0x3f005800, 0x3f036b20, 0x3f036b18
fixme:advapi:EventRegister {58a9201e-73b0-42ce-9821-7e134361bc70}, 0x3f005800, 0x3f036b58, 0x3f036b50
fixme:advapi:EventRegister {3fa9201e-73b0-43fe-9821-7e145359bc6f}, 0x3f005800, 0x3f036ae8, 0x3f036ae0
fixme:advapi:EventRegister {1432afee-73b0-42ce-9821-7e134361b433}, 0x3f005800, 0x3f036b90, 0x3f036b88
fixme:advapi:EventRegister {4372afee-73b0-42ce-9821-7e134361b519}, 0x3f005800, 0x3f036bc8, 0x3f036bc0
fixme:process:GetLogicalProcessorInformation ((nil),0x80e490): stub
fixme:process:GetLogicalProcessorInformation (0x810418,0x80e490): stub
wine: Call from 0x7bc49f80 to unimplemented function ADVAPI32.dll.StopTraceA, aborting
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:advapi:EventUnregister deadbeef: stub
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 80000100
fixme:advapi:RegisterEventSourceA ((null),"Steam Client Service"): stub
fixme:advapi:RegisterEventSourceW (L"",L"Steam Client Service"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0xc0000001,(nil),0x0001,0x00000000,0x80e778,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0xc0000001,(nil),0x0001,0x00000000,0x132c68,(nil)): stub
err:eventlog:ReportEventW L"Failed to load Steam Service library."
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:advapi:RegisterEventSourceA ((null),"Steam Client Service"): stub
fixme:advapi:RegisterEventSourceW (L"",L"Steam Client Service"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0002,0x0000,0x80000002,(nil),0x0001,0x00000000,0x33f820,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0002,0x0000,0x80000002,(nil),0x0001,0x00000000,0x1305c0,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
[/PHP]

---

