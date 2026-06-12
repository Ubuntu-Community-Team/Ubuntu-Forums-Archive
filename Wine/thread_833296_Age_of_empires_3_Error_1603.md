---
title: "Age of empires 3 Error 1603"
date: 2008-06-18
forum: Wine
---

### Post by Adnanius on 2008-06-18
Hi, 
I've been trying to install aoe3 (asian dynasties) for like a month, without results. I did a (large) research on google, copied all dlls, configured wine, ... it just dosent work. at last, I read something about aoe3 working in version 1.0 of wine, so I said I'll wait for it! And now I just got the 1.0 version, but it still dosent install!

The installation starts but then gives the famous "Error 1603 Consult Windows Installer Help (msi.chm) or MSDN for more information", while copying Age Of Empires 3\ Readme.rtf

Would anyone help me with this PLEASE?

---

### Post by cogadh on 2008-06-19
Run the install from the terminal and post the full output here.

---

### Post by Adnanius on 2008-06-19
here is the terminal's output:

```
adnanius@laptopi:~/AOE/AOEs/rld-aoea.iso01$ wine setup.exe 
fixme:advapi:LookupAccountNameW (null) L"adnanius" (nil) 0x33a2c4 (nil) 0x33a2bc 0x33a2c0 - stub
fixme:advapi:LookupAccountNameW (null) L"adnanius" 0x136860 0x33a2c4 0x135650 0x33a2bc 0x33a2c0 - stub
err:msi:ITERATE_DuplicateFiles Failed to copy file L"C:\\Program Files\\Common Files\\InstallShield\\Driver\\11\\Intel 32\\IDriver.exe" -> L"C:\\Program Files\\Common Files\\InstallShield\\Driver\\11\\Intel 32\\", last error 80
fixme:msi:ITERATE_DuplicateFiles We should track these duplicate files as well
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 2 ignored L"CreateFolder" table values
fixme:advapi:LookupAccountNameW (null) L"adnanius" (nil) 0x33ab48 (nil) 0x33ab40 0x33ab44 - stub
fixme:advapi:LookupAccountNameW (null) L"adnanius" 0x17f2f8 0x33ab48 0x17de30 0x33ab40 0x33ab44 - stub
fixme:reg:GetNativeSystemInfo (0x3300a4) using GetSystemInfo()
fixme:ole:CoInitializeSecurity (0x5302f8,-1,(nil),(nil),4,3,(nil),0,(nil)) - stub!
fixme:advapi:RegisterEventSourceA ((null),"IDriverT"): stub
fixme:advapi:RegisterEventSourceW (L"",L"IDriverT"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0x7e647988,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0x126ca0,(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:ole:PSFacBuf_CreateStub stubbing not implemented for ({00000010-0000-0000-c000-000000000046}) yet!
err:ole:marshal_object Failed to create an IRpcStubBuffer from IPSFactory for {00000010-0000-0000-c000-000000000046} with error 0x80004005
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
fixme:advapi:LookupAccountNameW (null) L"adnanius" (nil) 0x7d32cff4 (nil) 0x7d32cfec 0x7d32cff0 - stub
fixme:advapi:LookupAccountNameW (null) L"adnanius" 0x1b91090 0x7d32cff4 0x1b91828 0x7d32cfec 0x7d32cff0 - stub
fixme:ole:PSFacBuf_CreateStub stubbing not implemented for ({00000010-0000-0000-c000-000000000046}) yet!
err:ole:marshal_object Failed to create an IRpcStubBuffer from IPSFactory for {00000010-0000-0000-c000-000000000046} with error 0x80004005
err:rpc:I_RpcReceive we got fault packet with status 0x80004002
err:ole:ClientIdentity_QueryMultipleInterfaces IRemUnknown_RemQueryInterface failed with error 0x80004002
fixme:rpc:RpcMgmtWaitServerListen not waiting for server calls to finish
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:rpc:RpcImpersonateClient (0x22390d8): stub
fixme:rpc:RpcRevertToSelfEx (0x22390d8): stub
fixme:rpc:RpcImpersonateClient (0x2239ca8): stub
fixme:rpc:RpcRevertToSelfEx (0x2239ca8): stub
fixme:rpc:RpcImpersonateClient (0x223a678): stub
fixme:rpc:RpcRevertToSelfEx (0x223a678): stub
fixme:rpc:RpcImpersonateClient (0x223a678): stub
fixme:rpc:RpcRevertToSelfEx (0x223a678): stub
fixme:msi:msi_unimplemented_action_stub MsiUnpublishAssemblies -> 2 ignored L"MsiAssembly" table values
fixme:msi:msi_unimplemented_action_stub SelfUnregModules -> 1 ignored L"SelfReg" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 5 ignored L"CreateFolder" table values
fixme:rpc:RpcImpersonateClient (0x250ba18): stub
fixme:rpc:RpcRevertToSelfEx (0x250ba18): stub
err:msi:ready_media Cabinet not found: L"D:\\Disk2C~1.cab"
err:msi:ACTION_InstallFiles Failed to ready media
err:msi:ITERATE_Actions Execution halted, action L"InstallFinalize" returned 1603
```

---

### Post by cogadh on 2008-06-19
Well, at the very least, we know why you got that oh-so-informative Error 1603:
```
err:msi:ready_media Cabinet not found: L"D:\\Disk2C~1.cab"
```
The install is looking for a cab file from disk 2 and can't find it. Instead of using a mounted iso, try using the original game CDs, there may be a problem with the iso file that is presenting itself like this.

---

### Post by Adnanius on 2008-06-19
hi again, 
Thank you for your answer, it helped ! I haven't copied the contents of cd2 & 3 in the corresponding folder, now the game is installed. When I run it, it says that 'it seams that my computer have only 32MB of vga, and that aoe3 needs 64MB minimum'. 
Actually, I have an nvidia gforce4 440 Go, 64mb. 
How come it says that I only have 32 ?
Ps:  I tried both the restricted nvidia driver (legacy) and glx-nvidia

---

### Post by cogadh on 2008-06-19
Wine does not actually detect your video memory, but you can manually set it in Wine's registry. See the Wine [Useful Registry Keys](http://wiki.winehq.org/UsefulRegistryKeys) page for details on what keys to create.

---

### Post by Adnanius on 2008-06-20
I created the corresponding keys in the registry, but it didn't change. 
Then I tried changing the color depth in xorg: when I set it to 32, lunching the game tells me that 'It appears that I only have 8 MB' (and not 32MB as it used to tell. 
I tried the other 16mb, 256mb, and it doesn't work neither.
My current color depth is 24
Any suggestions ?

---

### Post by cogadh on 2008-06-20
Xorg doesn't do more that 24BPP color, so setting it to 32 would only cause more issues. You created the HKEY_CURRENT_USER/Software/Wine/Direct3D/VideoMemorySize key and it still reports the wrong video memory? That shouldn't be possible. Are you sure you created it correctly? In regedit, it should look,like this:

---

### Post by Adnanius on 2008-06-20
I did :-(

And here's the terminal's output :
```
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cfb830, 1, 0x2cfd990)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Wave Parser"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{D51BD5A1-7548-11CF-A520-0080C77EF58A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cfb830, 1, 0x2cfdde8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"File Source (Async.)"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E436EBB5-524F-11CE-9F53-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a760-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x2cfb808)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a761-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x2cfb808)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a762-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x2cfb810)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cfb810, 1, 0x2cfb828)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dsnoop:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D2-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({4efe2452-168a-11d1-bc76-00c04fb9453b}) pEnum(0x2cfb7e8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cfb7e8, 1, 0x2cfb800)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Midi Through"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({860bb310-5d01-11d0-bd3b-00a0c911ce86}) pEnum(0x2cfe1b8)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb41-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb46-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({e0f158e1-cb04-11d0-bd4e-00a0c911ce86}) pEnum(0x2cfb7b8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cfb7b8, 1, 0x2cfb7d0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"DirectSound: dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cfb7b8, 1, 0x2cfef60)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D1-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"ddraw.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dplayx.dll")
err:dplay:DPLAYX_ConstructData : unable to map static data into process memory space (487)
err:dplay:DPLAYX_ConstructData : unable to map static data into process memory space (487)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dpnet.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dinput.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dinput8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dsound.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dswave.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"d3d8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"d3d9.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dmband.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dmcompos.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dmime.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dmloader.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dmscript.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dmstyle.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dmsynth.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dmusic.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"devenum.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"quartz.dll")
fixme:win:EnumDisplayDevicesW ((null),0,0x33ed34,0x00000000), stub!
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({083863f1-70de-11d0-bd40-00a0c911ce86}) pEnum(0x2d04bf0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04bf0, 1, 0x2d04c08)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{1B544C20-FD0B-11CE-8C63-00AA0044B51E}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04bf0, 1, 0x2d04c20)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"MPEG-I Stream Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{336475D0-942A-11CE-A870-00AA002FEAB5}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04bf0, 1, 0x2d05098)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"ACM Wrapper"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{6A08CF80-0E18-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04bf0, 1, 0x2d056d0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{6BC1CFFA-8FC1-4261-AC22-CFB4CC38DB50}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04bf0, 1, 0x2d05cb0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{70E102B0-5556-11CE-97C0-00AA0055595A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04bf0, 1, 0x2d060d8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Audio Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04bf0, 1, 0x2d06500)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Null Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{C1F400A4-3F08-11D3-9F0B-006008039E37}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04bf0, 1, 0x2d06928)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Decompressor"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{CF49D4E0-1115-11CE-B03A-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04bf0, 1, 0x2d06d50)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Wave Parser"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{D51BD5A1-7548-11CF-A520-0080C77EF58A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04bf0, 1, 0x2d071a8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"File Source (Async.)"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E436EBB5-524F-11CE-9F53-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a760-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x2d04bc8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a761-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x2d04bc8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a762-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x2d04bd0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04bd0, 1, 0x2d04be8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dsnoop:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D2-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({4efe2452-168a-11d1-bc76-00c04fb9453b}) pEnum(0x2d04ba8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04ba8, 1, 0x2d04bc0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Midi Through"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({860bb310-5d01-11d0-bd3b-00a0c911ce86}) pEnum(0x2d07578)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb41-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb46-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({e0f158e1-cb04-11d0-bd4e-00a0c911ce86}) pEnum(0x2d04b78)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04b78, 1, 0x2d04b90)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"DirectSound: dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04b78, 1, 0x2d08320)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D1-27E5-11CE-875D-00608CB78066}"
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
^[[A^[[B^[[Aerr:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
adnanius@laptopi:~/.wine/drive_c/Program Files/Microsoft Games/Age of Empires III$ wine age3.exe 
err:ole:CoGetClassObject class {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} not registered
err:ole:CoGetClassObject no class object {529a9e6b-6587-4f23-ab9e-9c7d683e3c50} could be created for context 0x1
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1
fixme:imm:ImmReleaseContext (0x20036, 0x136d30): stub
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:imm:ImmGetOpenStatus (0x136d30): semi-stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f370,0x00000000), stub!
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ce3130,L"ddraw.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ce3130,L"dplayx.dll")
err:dplay:DPLAYX_ConstructData : unable to map static data into process memory space (487)
err:dplay:DPLAYX_ConstructData : unable to map static data into process memory space (487)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ce3130,L"dpnet.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ce3130,L"dinput.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ce3130,L"dinput8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ce3130,L"dsound.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ce3130,L"dswave.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ce3130,L"d3d8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ce3130,L"d3d9.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ce3130,L"dmband.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ce3130,L"dmcompos.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ce3130,L"dmime.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ce3130,L"dmloader.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ce3130,L"dmscript.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ce3130,L"dmstyle.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ce3130,L"dmsynth.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ce3130,L"dmusic.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ce3130,L"devenum.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ce3130,L"quartz.dll")
fixme:win:EnumDisplayDevicesW ((null),0,0x33edd8,0x00000000), stub!
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({083863f1-70de-11d0-bd40-00a0c911ce86}) pEnum(0x2ce8ef8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2ce8ef8, 1, 0x2ce9118)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{1B544C20-FD0B-11CE-8C63-00AA0044B51E}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2ce8ef8, 1, 0x2ce9130)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"MPEG-I Stream Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{336475D0-942A-11CE-A870-00AA002FEAB5}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2ce8ef8, 1, 0x2ce94f0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"ACM Wrapper"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{6A08CF80-0E18-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2ce8ef8, 1, 0x2ce9bf0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{6BC1CFFA-8FC1-4261-AC22-CFB4CC38DB50}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2ce8ef8, 1, 0x2cea1d8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{70E102B0-5556-11CE-97C0-00AA0055595A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2ce8ef8, 1, 0x2cea600)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Audio Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2ce8ef8, 1, 0x2ceaa28)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Null Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{C1F400A4-3F08-11D3-9F0B-006008039E37}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2ce8ef8, 1, 0x2ceae50)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Decompressor"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{CF49D4E0-1115-11CE-B03A-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2ce8ef8, 1, 0x2ceb278)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Wave Parser"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{D51BD5A1-7548-11CF-A520-0080C77EF58A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2ce8ef8, 1, 0x2ceb6d0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"File Source (Async.)"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E436EBB5-524F-11CE-9F53-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a760-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x2ce8e70)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a761-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x2ce8e70)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a762-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x2ce8ed8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2ce8ed8, 1, 0x2ce8ef0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dsnoop:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D2-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({4efe2452-168a-11d1-bc76-00c04fb9453b}) pEnum(0x2ce8eb0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2ce8eb0, 1, 0x2ce8ec8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Midi Through"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({860bb310-5d01-11d0-bd3b-00a0c911ce86}) pEnum(0x2cebaa0)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb41-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb46-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({e0f158e1-cb04-11d0-bd4e-00a0c911ce86}) pEnum(0x2ce8e80)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2ce8e80, 1, 0x2ce8e98)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"DirectSound: dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2ce8e80, 1, 0x2cec830)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D1-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ced5c0,L"ddraw.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ced5c0,L"dplayx.dll")
err:dplay:DPLAYX_ConstructData : unable to map static data into process memory space (487)
err:dplay:DPLAYX_ConstructData : unable to map static data into process memory space (487)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ced5c0,L"dpnet.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ced5c0,L"dinput.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ced5c0,L"dinput8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ced5c0,L"dsound.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ced5c0,L"dswave.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ced5c0,L"d3d8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ced5c0,L"d3d9.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ced5c0,L"dmband.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ced5c0,L"dmcompos.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ced5c0,L"dmime.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ced5c0,L"dmloader.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ced5c0,L"dmscript.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ced5c0,L"dmstyle.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ced5c0,L"dmsynth.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ced5c0,L"dmusic.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ced5c0,L"devenum.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2ced5c0,L"quartz.dll")
fixme:win:EnumDisplayDevicesW ((null),0,0x33ef04,0x00000000), stub!
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({083863f1-70de-11d0-bd40-00a0c911ce86}) pEnum(0x2cf2490)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cf2490, 1, 0x2cf24a8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{1B544C20-FD0B-11CE-8C63-00AA0044B51E}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cf2490, 1, 0x2cf24c0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"MPEG-I Stream Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{336475D0-942A-11CE-A870-00AA002FEAB5}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cf2490, 1, 0x2cf2938)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"ACM Wrapper"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{6A08CF80-0E18-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cf2490, 1, 0x2cf2f70)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{6BC1CFFA-8FC1-4261-AC22-CFB4CC38DB50}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cf2490, 1, 0x2cf3550)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{70E102B0-5556-11CE-97C0-00AA0055595A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cf2490, 1, 0x2cf3978)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Audio Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cf2490, 1, 0x2cf3da0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Null Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{C1F400A4-3F08-11D3-9F0B-006008039E37}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cf2490, 1, 0x2cf41c8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Decompressor"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{CF49D4E0-1115-11CE-B03A-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cf2490, 1, 0x2cf45f0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Wave Parser"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{D51BD5A1-7548-11CF-A520-0080C77EF58A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cf2490, 1, 0x2cf4a48)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"File Source (Async.)"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E436EBB5-524F-11CE-9F53-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a760-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x2cf2468)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a761-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x2cf2468)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a762-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x2cf2470)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cf2470, 1, 0x2cf2488)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dsnoop:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D2-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({4efe2452-168a-11d1-bc76-00c04fb9453b}) pEnum(0x2cf2448)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cf2448, 1, 0x2cf2460)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Midi Through"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({860bb310-5d01-11d0-bd3b-00a0c911ce86}) pEnum(0x2cf4e18)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb41-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb46-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({e0f158e1-cb04-11d0-bd4e-00a0c911ce86}) pEnum(0x2cf2418)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cf2418, 1, 0x2cf2430)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"DirectSound: dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cf2418, 1, 0x2cf5bc0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D1-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cf6960,L"ddraw.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cf6960,L"dplayx.dll")
err:dplay:DPLAYX_ConstructData : unable to map static data into process memory space (487)
err:dplay:DPLAYX_ConstructData : unable to map static data into process memory space (487)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cf6960,L"dpnet.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cf6960,L"dinput.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cf6960,L"dinput8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cf6960,L"dsound.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cf6960,L"dswave.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cf6960,L"d3d8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cf6960,L"d3d9.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cf6960,L"dmband.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cf6960,L"dmcompos.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cf6960,L"dmime.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cf6960,L"dmloader.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cf6960,L"dmscript.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cf6960,L"dmstyle.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cf6960,L"dmsynth.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cf6960,L"dmusic.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cf6960,L"devenum.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cf6960,L"quartz.dll")
fixme:win:EnumDisplayDevicesW ((null),0,0x33e834,0x00000000), stub!
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({083863f1-70de-11d0-bd40-00a0c911ce86}) pEnum(0x2cfb830)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cfb830, 1, 0x2cfb848)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{1B544C20-FD0B-11CE-8C63-00AA0044B51E}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cfb830, 1, 0x2cfb860)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"MPEG-I Stream Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{336475D0-942A-11CE-A870-00AA002FEAB5}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cfb830, 1, 0x2cfbcd8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"ACM Wrapper"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{6A08CF80-0E18-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cfb830, 1, 0x2cfc310)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{6BC1CFFA-8FC1-4261-AC22-CFB4CC38DB50}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cfb830, 1, 0x2cfc8f0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{70E102B0-5556-11CE-97C0-00AA0055595A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cfb830, 1, 0x2cfcd18)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Audio Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cfb830, 1, 0x2cfd140)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Null Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{C1F400A4-3F08-11D3-9F0B-006008039E37}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cfb830, 1, 0x2cfd568)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Decompressor"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{CF49D4E0-1115-11CE-B03A-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cfb830, 1, 0x2cfd990)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Wave Parser"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{D51BD5A1-7548-11CF-A520-0080C77EF58A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cfb830, 1, 0x2cfdde8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"File Source (Async.)"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E436EBB5-524F-11CE-9F53-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a760-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x2cfb808)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a761-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x2cfb808)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a762-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x2cfb810)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cfb810, 1, 0x2cfb828)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dsnoop:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D2-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({4efe2452-168a-11d1-bc76-00c04fb9453b}) pEnum(0x2cfb7e8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cfb7e8, 1, 0x2cfb800)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Midi Through"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({860bb310-5d01-11d0-bd3b-00a0c911ce86}) pEnum(0x2cfe1b8)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb41-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb46-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({e0f158e1-cb04-11d0-bd4e-00a0c911ce86}) pEnum(0x2cfb7b8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cfb7b8, 1, 0x2cfb7d0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"DirectSound: dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2cfb7b8, 1, 0x2cfef60)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D1-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"ddraw.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dplayx.dll")
err:dplay:DPLAYX_ConstructData : unable to map static data into process memory space (487)
err:dplay:DPLAYX_ConstructData : unable to map static data into process memory space (487)
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dpnet.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dinput.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dinput8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dsound.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dswave.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"d3d8.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"d3d9.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dmband.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dmcompos.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dmime.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dmloader.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dmscript.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dmstyle.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dmsynth.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"dmusic.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"devenum.dll")
fixme:dxdiag:DXDiag_AddFileDescContainer (0x2cffd20,L"quartz.dll")
fixme:win:EnumDisplayDevicesW ((null),0,0x33ed34,0x00000000), stub!
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({083863f1-70de-11d0-bd40-00a0c911ce86}) pEnum(0x2d04bf0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04bf0, 1, 0x2d04c08)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{1B544C20-FD0B-11CE-8C63-00AA0044B51E}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04bf0, 1, 0x2d04c20)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"MPEG-I Stream Splitter"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{336475D0-942A-11CE-A870-00AA002FEAB5}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04bf0, 1, 0x2d05098)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"ACM Wrapper"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{6A08CF80-0E18-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04bf0, 1, 0x2d056d0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{6BC1CFFA-8FC1-4261-AC22-CFB4CC38DB50}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04bf0, 1, 0x2d05cb0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Video Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{70E102B0-5556-11CE-97C0-00AA0055595A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04bf0, 1, 0x2d060d8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Audio Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04bf0, 1, 0x2d06500)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Null Renderer"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{C1F400A4-3F08-11D3-9F0B-006008039E37}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04bf0, 1, 0x2d06928)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"AVI Decompressor"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{CF49D4E0-1115-11CE-B03A-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04bf0, 1, 0x2d06d50)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Wave Parser"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{D51BD5A1-7548-11CF-A520-0080C77EF58A}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04bf0, 1, 0x2d071a8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"File Source (Async.)"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E436EBB5-524F-11CE-9F53-0020AF0BA770}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a760-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x2d04bc8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a761-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x2d04bc8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({33d9a762-90c8-11d0-bd43-00a0c911ce86}) pEnum(0x2d04bd0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04bd0, 1, 0x2d04be8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dsnoop:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D2-27E5-11CE-875D-00608CB78066}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({4efe2452-168a-11d1-bc76-00c04fb9453b}) pEnum(0x2d04ba8)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04ba8, 1, 0x2d04bc0)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"Midi Through"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{07B65360-C445-11CE-AFDE-00AA006C14F4}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({860bb310-5d01-11d0-bd3b-00a0c911ce86}) pEnum(0x2d07578)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb41-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({cc7bfb46-f175-11d1-a392-00e0291f3959}) pEnum((nil))
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        ClassEnumerator for clsid({e0f158e1-cb04-11d0-bd4e-00a0c911ce86}) pEnum(0x2d04b78)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04b78, 1, 0x2d04b90)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"DirectSound: dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{79376820-07D0-11CF-A24D-0020AFD79767}"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        IEnumMoniker_Next(0x2d04b78, 1, 0x2d08320)
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Name:L"dmix:0"
fixme:dxdiag:DXDiag_InitDXDiagDirectShowFiltersContainer        Clsid:L"{E30629D1-27E5-11CE-875D-00608CB78066}"
err:ole:CoGetClassObject class {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} not registered
err:ole:CoGetClassObject no class object {ebb08c45-6c4a-4fdc-ae53-4eb8c4c7db8e} could be created for context 0x1

```

---

### Post by Adnanius on 2008-06-23
Hellllllo

---

