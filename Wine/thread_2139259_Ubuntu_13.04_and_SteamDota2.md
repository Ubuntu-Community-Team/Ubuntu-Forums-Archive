---
title: "Ubuntu 13.04 and Steam/Dota2"
date: 2013-04-26
forum: Wine
---

### Post by ib4ngsh33p on 2013-04-26
when i upgraded to 13.04 from 12.04 i can no longer launch DOTA2. it blacks out my screen, flashes a massively low resolution of the corner of my screen, and will just sit there until i kill the process. 

i followed the WineDB process for installing Steam/DotA2, with no luck. any insight would be helpful

output from terminal:
err:winediag:xrandr12_init_modes Broken NVIDIA RandR detected, falling back to RandR 1.0. Please consider using the Nouveau driver instead.
fixme:advapi:EventRegister {47a9201e-73b0-42ce-9821-7e134361bc6f}, 0x3f005530, 0x3f036b40, 0x3f036b38
fixme:advapi:EventRegister {58a9201e-73b0-42ce-9821-7e134361bc70}, 0x3f005530, 0x3f036b78, 0x3f036b70
fixme:advapi:EventRegister {3fa9201e-73b0-43fe-9821-7e145359bc6f}, 0x3f005530, 0x3f036b08, 0x3f036b00
fixme:advapi:EventRegister {1432afee-73b0-42ce-9821-7e134361b433}, 0x3f005530, 0x3f036bb0, 0x3f036ba8
fixme:advapi:EventRegister {4372afee-73b0-42ce-9821-7e134361b519}, 0x3f005530, 0x3f036be8, 0x3f036be0
fixme:process:SetProcessShutdownParameters (000003ff, 00000000): partial stub.
fixme:iphlpapi:NotifyAddrChange (Handle 0x5dad6bc, overlapped 0x53fb478): stub
fixme:winsock:WSALookupServiceBeginW (0x5dad7bc 0x00000ff0 0x5dad804) Stub!
[0426/102002:ERROR:network_change_notifier_win.cc(111)] WSALookupServiceBegin failed with: 8
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:appbar:SHAppBarMessage unknown msg: 4
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=3): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=1): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=0): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=2): stub
fixme:appbar:SHAppBarMessage unknown msg: 4
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=3): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=1): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=0): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=2): stub
fixme:appbar:SHAppBarMessage unknown msg: 4
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=3): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=1): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=0): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=2): stub
fixme:appbar:SHAppBarMessage unknown msg: 4
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=3): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=1): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=0): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=2): stub
fixme:appbar:SHAppBarMessage unknown msg: 4
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETSTATE): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=3): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=1): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=0): stub
fixme:appbar:handle_appbarmessage SHAppBarMessage(ABM_GETAUTOHIDEBAR, hwnd=(nil), edge=2): stub
err:ntdll:RtlpWaitForCriticalSection section 0xa37c24 "?" wait timed out in thread 002d, blocked by 002e, retrying (60 sec)
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
CClientSteamContext logged on = 1
ConVarRef rr_debugresponses doesn't point to an existing ConVar
Could not get IReplayDirector interface from library server.dllGame.dll loaded for "Dota 2"
fixme:thread:SetThreadIdealProcessor (0xfffffffe): stub
fixme:thread:SetThreadIdealProcessor (0x2b8): stub
fixme:thread:SetThreadIdealProcessor (0x2d8): stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:imm:ImmReleaseContext (0x30156, 0x1107f8b8): stub
err:ole:CoInitializeEx Attempt to change threading model of this apartment from apartment threaded to multi-threaded
fixme:pulse:AudioSessionControl_RegisterAudioSessionNotification (0x18867068)->(0x1b558acc) - stub
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Audio",0x1b75e958): stub
fixme:avrt:AvSetMmThreadPriority (0x12345678)->(1) stub
^Cfixme:console:CONSOLE_DefaultHandler Terminating process 25 on event 0
fixme:console:CONSOLE_DefaultHandler Terminating process 8 on event 0
fixme:advapi:StopTraceA (0, "Steam Event Tracing", 0x10f6e54c) stub
fixme:advapi:CloseTrace ffffffff: stub
fixme:iphlpapi:CancelIPChangeNotify (overlapped 0x53fb478): stub
Assert( Assertion Failed: m_hSteamPipe == NULL ):..\common\steamservice.cpp:49

err:winediag:xrandr12_init_modes Broken NVIDIA RandR detected, falling back to RandR 1.0. Please consider using the Nouveau driver instead.
fixme:advapi:EventRegister {47a9201e-73b0-42ce-9821-7e134361bc6f}, 0x3f005530, 0x3f036b40, 0x3f036b38
fixme:advapi:EventRegister {58a9201e-73b0-42ce-9821-7e134361bc70}, 0x3f005530, 0x3f036b78, 0x3f036b70
fixme:advapi:EventRegister {3fa9201e-73b0-43fe-9821-7e145359bc6f}, 0x3f005530, 0x3f036b08, 0x3f036b00
fixme:advapi:EventRegister {1432afee-73b0-42ce-9821-7e134361b433}, 0x3f005530, 0x3f036bb0, 0x3f036ba8
fixme:advapi:EventRegister {4372afee-73b0-42ce-9821-7e134361b519}, 0x3f005530, 0x3f036be8, 0x3f036be0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
err:ntdll:RtlpWaitForCriticalSection section 0x7bcc6a60 "loader.c: loader_section" wait timed out in thread 0009, blocked by 0074, retrying (60 sec)

---

