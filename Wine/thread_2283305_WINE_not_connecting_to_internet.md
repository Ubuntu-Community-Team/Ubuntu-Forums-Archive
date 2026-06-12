---
title: "WINE not connecting to internet"
date: 2015-06-20
forum: Wine
---

### Post by williamcathey on 2015-06-20
At some point this past week, my WINE stopped connecting to the internet. I'm using Ubuntu 14.04.2, and wine version 1:1.6.2-0ubuntu4. It worked last Saturday, but not today. I'm able to connect to the internet through my main browser (I'm using it to post this). I tried 'wine iexplore.exe' to test the connection and this is what appeared on the terminal window while it was running:

```
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
err:service:service_send_start_message service L"Apple Mobile Device" failed to start
fixme:service:scmdatabase_autostart_services Auto-start service L"Apple Mobile Device" failed to start: 1053
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x79e53c,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x132410,(nil)): stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:iphlpapi:CreateIpForwardEntry (pRoute 0x79e908): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x79e53c,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x1328c8,(nil)): stub
fixme:service:EnumServicesStatusW resume handle not supported
fixme:service:EnumServicesStatusW resume handle not supported
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x79e53c,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x1328c8,(nil)): stub
fixme:netapi32:NetGetJoinInformation Semi-stub (null) 0x79e5f4 0x79e5ec
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000064,(nil),0x0001,0x00000000,0x79dd38,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000064,(nil),0x0001,0x00000000,0x1328c8,(nil)): stub
err:eventlog:ReportEventW L"mDNSCoreReceiveResponse: Received from 192.168.1.103:5353   11 Billy-Lappy.local. HINFO I686\00c2\00a6LINUX"
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000064,(nil),0x0001,0x00000000,0x79dd3c,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000064,(nil),0x0001,0x00000000,0x1328c8,(nil)): stub
err:eventlog:ReportEventW L"mDNSCoreReceiveResponse: ProbeCount 2; will deregister    4 Billy-Lappy.local. Addr 192.168.1.103"
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000064,(nil),0x0001,0x00000000,0x79dcac,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000064,(nil),0x0001,0x00000000,0x1328c8,(nil)): stub
err:eventlog:ReportEventW L"Local Hostname Billy-Lappy.local already in use; will try Billy-Lappy-2.local instead"
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000064,(nil),0x0001,0x00000000,0x79dd38,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000064,(nil),0x0001,0x00000000,0x1328c8,(nil)): stub
err:eventlog:ReportEventW L"mDNSCoreReceiveResponse: Received from 192.168.1.103:5353   19 103.1.168.192.in-addr.arpa. PTR Billy-Lappy.local."
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x00000064,(nil),0x0001,0x00000000,0x79dd40,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x00000064,(nil),0x0001,0x00000000,0x1328c8,(nil)): stub
err:eventlog:ReportEventW L"mDNSCoreReceiveResponse: Unexpected conflict discarding   21 103.1.168.192.in-addr.arpa. PTR Billy-Lappy-2.local."
fixme:ole:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
fixme:ole:CoResumeClassObjects stub
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:ras:RasEnumConnectionsW (0x13ebb0,0x90d7d0,0x76c623e4),stub!
fixme:ras:RasEnumConnectionsW RAS support is not implemented! Configure program to use LAN connection/winsock instead!
fixme:service:EnumServicesStatusW resume handle not supported
fixme:ras:RasEnumEntriesW ((nil),(null),0x17bad0,0x90e000,0x17b7bc),stub!
err:secur32:schan_AcquireClientCredentials Could not find matching protocol
fixme:crypt:CRYPT_RegControl CERT_STORE_CTRL_AUTO_RESYNC: stub
fixme:crypt:CRYPT_RegControl CERT_STORE_CTRL_AUTO_RESYNC: stub
fixme:ieframe:handle_navigation_error Navigate to error page
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:ieframe:handle_navigation_error Navigate to error page
fixme:ieframe:bind_to_object BindToObject failed: 800401e4
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:ieframe:handle_navigation_error Navigate to error page
fixme:ieframe:bind_to_object BindToObject failed: 800401e4



```

---

### Post by brad39 on 2015-06-22
Have you tried compiling WINE yourself? I had run into a similar issue and that seemed to work for me.

---

### Post by williamcathey on 2015-07-03
I wouldn't even know where to start for that.

Anyway, new information:  I tried just wiping the computer and reinstalled.  Wine connected at first, but when I used 'winetricks wininet' to fix a problem with Hero Lab not getting updates, wine stopped connecting to the internet, so I'm right back to square one.

---

