---
title: "WINE - mounted img - incorrect CD error - pls help!?"
date: 2012-09-02
forum: Wine
---

### Post by captainzeal on 2012-09-02
Hi guys thx for the wonderful forum. i'm now growing very much attached to ubuntu, and have downloaded for myself an ubuntu guide. i've managed to get so far using previous on the internet, but now i really need your help! anyways, this one is a little tricky:



[LIST=1]
[*]basically i've got a windows program that i've downloaded. i've extracted the archived files and now i've got an img file which i've mounted.
[*]i've mounted it using AcetoneISO. I've gone to the "virtual drive" that acetoneiso creates (home/virtualdrive/1) , to actually be able to use the img file.
[*]Using WINE configuration GUI, in the "drives" tab , i've set the "virtualdrive" folder to the a: drive, and I have also let wine know that the "a:" drive is a cd-rom drive.
[*]now within the virtual drive folder, within the folder "1", where all the img file is mounted in an intelligible form, there is a windows executable file. it is called: "METT-Program-Player.exe". I want to run this file so i can use the METT program (which is a windows based program) in Linux, through WINE.
[*]The problem: When I i right click and say "open program using windows WINE launcher" it comes up with some sort of error message saying: incorrect CD is used (Please insert the correct CD Rom)
[/LIST]

Now i've managed to WINE the executable file and the terminal's come up with the following (which I have no idea what it means):

fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:win:RegisterDeviceNotificationA (hwnd=0x13d960, filter=0xc9e9d4,flags=0x00000001) returns a fake device notification handle!
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER: unimplemented WSARecvMsg
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:iphlpapi:DeleteIpForwardEntry (pRoute 0x79e988): stub
fixme:iphlpapi:CreateIpForwardEntry (pRoute 0x79e9c0): stub
fixme:service:EnumServicesStatusW 0x126c08 type=30 state=3 (nil) 0 0x79e7e8 0x79e7f0 0x79e7e4
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x79e5f0,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000064,(nil),0x0001,0x00000000,0x126940,(nil)): stub
fixme:netapi32:NetGetJoinInformation Stub (null) 0x79e6a8 0x79e6a0
wine: cannot find L"C:\\windows\\system32\\gearsec.exe"
fixme:winsock:WSAIoctl WS_SIO_UDP_CONNRESET stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER: unimplemented WSARecvMsg


Pls does anybody have any ideas on how i can fix this? I'm a n00b still trying to get to grips with Ubuntu. thx everyone for your support. I wish i was as knowledgeable as u guys....

once again thx very much.

captainzeal

---

### Post by oldos2er on 2012-09-02
Moved to Wine.

---

