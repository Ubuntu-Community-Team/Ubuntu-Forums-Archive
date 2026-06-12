---
title: "Hitman Blood Money in Wine"
date: 2016-05-09
forum: Wine
---

### Post by bluemewgaming on 2016-05-09
I'm currently using Lubuntu 15.04

I've never used this forum before so excuse my ignorance through this process.

Hitman Blood Money has only run completely smoothly once on my computer, and that's when I install it. Afterwards, it will boot to a screen like this: [IMG]https://i.sli.mg/ht0kaG.png[/IMG]

(Notice how it's completely invisible and is mimicing what shows up on the screen.

I decided to launch through the terminal and got this message:
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x54df10,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x3d070,(nil)): stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000013
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x54df10,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x3d8f0,(nil)): stub
fixme:service:EnumServicesStatusW resume handle not supported
fixme:service:EnumServicesStatusW resume handle not supported
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x54df10,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x3d8f0,(nil)): stub
fixme:netapi32:NetGetJoinInformation Semi-stub (null) 0x54df88 0x54df80
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IPV6 optname 0x00000013
err:module:import_dll Library dbghelp.dll (which is needed by L"C:\\windows\\system32\\mscoree.dll") not found
err:module:import_dll Library mscoree.dll (which is needed by L"C:\\windows\\Microsoft.NET\\Framework\\v4.0.30319\\mscorsvw.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\Microsoft.NET\\Framework\\v4.0.30319\\mscorsvw.exe" failed, status c0000135
err:service:service_send_start_message service L"clr_optimization_v4.0.30319_32" failed to start
fixme:service:scmdatabase_autostart_services Auto-start service L"clr_optimization_v4.0.30319_32" failed to start: 1053
err:module:import_dll Library MSVCR120_CLR0400.dll (which is needed by L"C:\\windows\\Microsoft.NET\\Framework64\\v4.0.30319\\mscorsvw.exe") not found
err:module:import_dll Library dbghelp.dll (which is needed by L"C:\\windows\\system32\\mscoree.dll") not found
err:module:import_dll Library mscoree.dll (which is needed by L"C:\\windows\\Microsoft.NET\\Framework64\\v4.0.30319\\mscorsvw.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\Microsoft.NET\\Framework64\\v4.0.30319\\mscorsvw.exe" failed, status c0000135
err:service:service_send_start_message service L"clr_optimization_v4.0.30319_64" failed to start
fixme:service:scmdatabase_autostart_services Auto-start service L"clr_optimization_v4.0.30319_64" failed to start: 1053
fixme:service:scmdatabase_autostart_services Auto-start service L"PnkBstrA" failed to start: 2
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000064,(nil),0x0001,0x00000000,0x54d420,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000064,(nil),0x0001,0x00000000,0x3d8f0,(nil)): stub
err:eventlog:ReportEventW L"mDNSCoreReceiveResponse: Received from 192.168.1.18:5353   13 bluemew-home.local. HINFO X86_64\00c2\00a6LINUX"
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000064,(nil),0x0001,0x00000000,0x54d420,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000064,(nil),0x0001,0x00000000,0x3d8f0,(nil)): stub
err:eventlog:ReportEventW L"mDNSCoreReceiveResponse: ProbeCount 2; will deregister    4 bluemew-home.local. Addr 192.168.1.18"
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000064,(nil),0x0001,0x00000000,0x54d330,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000064,(nil),0x0001,0x00000000,0x3d8f0,(nil)): stub
err:eventlog:ReportEventW L"Local Hostname bluemew-home.local already in use; will try bluemew-home-2.local instead"
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000064,(nil),0x0001,0x00000000,0x54d420,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000064,(nil),0x0001,0x00000000,0x3d8f0,(nil)): stub
err:eventlog:ReportEventW L"mDNSCoreReceiveResponse: Received from 192.168.1.18:5353   20 18.1.168.192.in-addr.arpa. PTR bluemew-home.local."
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000064,(nil),0x0001,0x00000000,0x54d420,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000064,(nil),0x0001,0x00000000,0x3d8f0,(nil)): stub
err:eventlog:ReportEventW L"mDNSCoreReceiveResponse: Unexpected conflict discarding   22 18.1.168.192.in-addr.arpa. PTR bluemew-home-2.local."
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000064,(nil),0x0001,0x00000000,0x54d420,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000064,(nil),0x0001,0x00000000,0x3d8f0,(nil)): stub
err:eventlog:ReportEventW L"mDNSCoreReceiveResponse: Received from 192.168.1.18:5353   20 6.4.6.c.1.0.e.f.f.f.5.e.7.6.2.d.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa. PTR bluemew-home.local."
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000064,(nil),0x0001,0x00000000,0x54d420,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000064,(nil),0x0001,0x00000000,0x3d8f0,(nil)): stub
err:eventlog:ReportEventW L"mDNSCoreReceiveResponse: Unexpected conflict discarding   22 6.4.6.C.1.0.E.F.F.F.5.E.7.6.2.D.0.0.0.0.0.0.0.0.0.0.0.0.0.8.E.F.ip6.arpa. PTR bluemew-home-2.local."
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec88,0x00000000), stub!
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1024x768x32 @0! (XRandR 1.2)
err:seh:setup_exception_record stack overflow 1644 bytes in thread 0009 eip 0045503c esp 00240cc4 stack 0x240000-0x241000-0x340000
Terminated
[email]bluemewgaming@bluemew-home:~/.wine[/email]/drive_c/Program Files (x86)/Eidos/Hitman Blood Money$ fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x54df10,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x3d8f0,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub


If anyone here could help me I'd appreciate it.

---

### Post by sweldon001 on 2016-05-12
Run in terminal Wine wintricks .. then install all [URL="https://www.therepopulation.com/wiki/lib/exe/fetch.php/repop_linux_008.png"]https://www.therepopulation.com/wiki/lib/exe/fetch.php/repop_linux_008.png 
[/URL]Meaning all direct X thing and  everything slowly in listed item, but remember most Adobe and some fonts don't always work on install and have to manually load / downloaded and run in switch method in wine indiviually.

---

