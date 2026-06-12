---
title: "Wireless Problems with Wine and City of Heroes"
date: 2007-11-30
forum: Wine
---

### Post by lightoverflow on 2007-11-30
Let me preface this by saying I've got the MadWiFi drivers for ubuntu and my wireless works there, but I seem to be having a problem where wine is sporadically recognizing my wireless connection.

Tried to run City of Heroes through wine only to have it kick back an error (within the program) saying that it couldn't connect to the login server. It does, however, connect to the update server fine. I then plugged into a wired connection and everything worked flawlessly.

I'm running Gutsy Gibbon (7.10) on a Macbook Pro (C2D, 17") and am using the latest Wine (0.9.49).

As I'm new to this whole thing, any help would be appreciated! :)

EDIT: Hmmm... It's working. Now to see if it works consistently.

---

### Post by cogadh on 2007-12-02
I'm on an "Unanswered Posts" quest and I was wondering, is this still a problem?

---

### Post by lightoverflow on 2007-12-02
Everything seems to be working great, thanks for asking!

---

### Post by lightoverflow on 2007-12-11
This is starting to happen again, more frequently this time. It'll also disconnect me from the game on occasion.

I don't think it has to do with my wireless signal as it's always worked on a windows laptop that I've used in the past.

---

### Post by graabein on 2007-12-16
According to [this link]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2980&iTestingId=16554") City of Heroes now works with Wine 0.9.50+ and I want to try it myself, but I have two problems;

[LIST=1]
[*]I play on US servers but bought the EU version so I need to get the other CohUpdater.exe file (US)
[*]The updater (EU) crashes with a segmentation fault when I run it
[/LIST]

```
Connected
checksum: 1257472 {e33077a7 2189014f fac11000 edd19650}
Patching project: Coh   Install Dir:  c:\Program Files\City of Heroes         
checksumLoad returned 1
Verifying checksum
Checksum Verify succeeded, requesting patch
Handling full manifest                                                        
Fixing files: piggs/geom.pigg
Error calling setsockopt, ending socket buffer size is not what we told it! (16384!=32768)
Error calling setsockopt, ending socket buffer size is not what we told it! (32768!=65536)
Error calling setsockopt, ending socket buffer size is not what we told it! (65536!=131072)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value dest (1)
fixme:dbghelp:SymInitializeW what to do ??
Segmentation fault (core dumped)
```

---

### Post by graabein on 2007-12-17
I located the US-version of CohUpdater.exe [here]("ftp://client.coh.com/US/") but I still don't get it to install.

```
wine CohUpdater.exe 
Processing argument list:
Patchserver: cohupdate.coh.com
US locale
fixme:shdocvw:PersistStorage_InitNew (0x12fab8)->(0x511058)
fixme:shdocvw:WebBrowser_QueryInterface (0x12fab8)->({0000011e-0000-0000-c000-000000000046} 0x7cdbf34c) interface not supported
fixme:shdocvw:OleObject_SetHostNames (0x12fab8)->(L"My Host Name", (null))
fixme:iphlpapi:NotifyAddrChange (Handle 0x7c87b9f8, overlapped 0x7c87b9dc): stub
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x12fb4c)->((null) 1 0x7cdbf03c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fb4c)->((null) 25 2 0x7cdbf050 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fb4c)->((null) 26 2 0x7cdbf050 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x12fb4c)->(0x7cdbf08c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fb4c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x7cdbf148 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x1316d8)->(L"" L"" 0 0x7cdbf17c)
fixme:shdocvw:BindStatusCallback_GetBindInfo (0x1316d8)->(0x7cdbf180 0x7cdbf190)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fb4c)->((null) 29 2 0x7cdbeec8 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x12fb4c)
fixme:shdocvw:ClientSite_GetContainer (0x12fb4c)->(0x7cdbedb4)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x12fb4c)->(0xb7e37109)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fb4c)->((null) 25 2 0x7cdbece8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fb4c)->((null) 26 2 0x7cdbece8 (nil))
Connecting to 216.107.254.194 : 6994...
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fb4c)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fb4c)->((null) 28 2 0x7cdbed40 (nil))
Connected
checksum: 1257472 {e33077a7 2189014f fac11000 edd19650}
Patching project: Coh   Install Dir:  c:\Program Files\City of Heroes         
checksumLoad returned 1
Verifying checksum
Checksum Verify succeeded, requesting patch
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fb4c)->((null) 26 2 0x7cdbeea8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fb4c)->((null) 29 2 0x7cdbeeb8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fb4c)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12fb4c)->((null) 35 0 (nil) (nil))
fixme:shdocvw:InPlaceFrame_SetStatusText (0x12fb4c)->(0x7cdbfcd5)
Handling full manifest                                                        
Fixing files: piggs/geom.pigg
Error calling setsockopt, ending socket buffer size is not what we told it! (16384!=32768)
Error calling setsockopt, ending socket buffer size is not what we told it! (32768!=65536)
Error calling setsockopt, ending socket buffer size is not what we told it! (65536!=131072)
2007-12-17 08:35:21 PROGRAM CRASH OCCURRED!
wine: Unhandled page fault on write access to 0x00000000 at address 0x4319b2 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x004319b2).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:004319b2 ESP:0033cd34 EBP:00000468 EFLAGS:00010202(   - 00      - -RI1)
 EAX:00000001 EBX:018a89d0 ECX:00000000 EDX:00000000
 ESI:0055a6c0 EDI:000004e4
Stack dump:
0x0033cd34:  00838928 018a89d0 0055a6c0 00000001
0x0033cd44:  00000001 00000001 00000004 00000000
0x0033cd54:  009870c0 000004e0 000005c0 00002700
0x0033cd64:  00000000 00000000 00000000 00000000
0x0033cd74:  00431da9 018a89d0 0055a6c0 0033cec8
0x0033cd84:  0033cec8 7b8b0888 0055a6c0 00000000
Backtrace:
=>1 0x004319b2 in cohupdater (+0x319b2) (0x00000468)
  2 0x00000000 (0x00000000)
```


Update: OK installed [latest version of Wine]("http://wine.budgetdedicated.com/archive/index.html") 0.9.51 and the installer is now running...

---

### Post by graabein on 2007-12-18
:popcorn:

Yep! Got it to work. 

Not 100% error free but it's close. I'm yet to try all the different settings but I assume it's not going to help much, considering [these reports]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=2980") on [http://appdb.winehq.org]("http://appdb.winehq.org").

So I guess I'll play from Ubuntu for a while and see how it works out with no costume changes. It's a bit sad cause it is a rather big part of the game, at least for me. That means my Windows XP partition will keep hanging around... ](*,)

---

