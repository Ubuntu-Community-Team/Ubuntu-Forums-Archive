---
title: "Save PDF does not work in Adobe Reader 10.1.4"
date: 2013-10-09
forum: Wine
---

### Post by elang on 2013-10-09
I installed Adobe Reader 10.1.4 on wine1.6. I am unable to save edits like comments and highlights.

To debug, I ran AcroRd32 from the wineprefix installed directory and got this as the output:

```

fixme: advapi: RegisterEventSourceW ((null),L"AdobeARMservice"):  stub
fixme: advapi: ReportEventW (0xcafe4242,0x0004,0x0000,0x00000000,(nil),0x0001,0x00000000,0x60e70c,(nil)):  stub
fixme: advapi: DeregisterEventSource (0xcafe4242) stub
fixme: process: SetProcessDEPPolicy (1):  stub
fixme: heap: HeapSetInformation (nil) 1 (nil) 0
fixme: advapi: CreateRestrictedToken (0xc4, 0x2, 3, 0xd20e10, 19, 0xce57e0, 4, 0xce55a8, 0x33ef9c):  stub
fixme: ntdll: NtSetInformationToken unimplemented class 25
fixme: wer: WerRegisterMemoryBlock (0x1624b0 72) stub
fixme: keyboard: X11DRV_MapVirtualKeyEx keyboard layout (nil) is not supported
fixme: keyboard: X11DRV_MapVirtualKeyEx keyboard layout (nil) is not supported
fixme: msvcp: _Locinfo__Locinfo_ctor_cat_cstr (0x33ebbc 1 C) semi-stub
fixme: ole: RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
fixme: ntdll: NtLockFile I/O completion on lock not implemented yet
fixme: ole: CoResumeClassObjects stub
fixme: wer: WerRegisterFile (L"Z: \\media\\elan\\elan\\Dropbox\\Dropbox\\Current Sem Courses\\pom\\management 11th edition (robbins).pdf", 1, 0) stub!
err: ntdll: NtQueryInformationToken Unhandled Token Information class 11!
fixme: keyboard: X11DRV_MapVirtualKeyEx keyboard layout (nil) is not supported
fixme: keyboard: X11DRV_MapVirtualKeyEx keyboard layout (nil) is not supported
err: ole: CoGetClassObject class {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} not registered
err: ole: create_server class {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} not registered
fixme: ole: CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err: ole: CoGetClassObject no class object {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} could be created for context 0x15
fixme: font: freetype_SelectFont Untranslated charset 123
err: ole: CoGetClassObject class {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} not registered
err: ole: create_server class {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} not registered
fixme: ole: CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err: ole: CoGetClassObject no class object {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} could be created for context 0x15
fixme: commdlg: GetFileName95 Flags 0x00010000 not yet implemented
fixme: ntdll: NtQueryInformationToken QueryInformationToken( ..., TokenElevationType, ...) semi-stub
fixme: ole: CoInitializeSecurity ((nil),-1,(nil),(nil),2,3,(nil),0,(nil)) - stub!
fixme: ole: CoInitializeSecurity ((nil),-1,(nil),(nil),1,3,(nil),0,(nil)) - stub!
fixme: ole: RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
fixme: qmgr: BITS_IBackgroundCopyJob_GetPriority Not implemented
fixme: qmgr: BITS_IBackgroundCopyJob_SetPriority (0x144990,0x00000001) stub
fixme: qmgr: BITS_IBackgroundCopyJob_GetPriority Not implemented
fixme: qmgr: BITS_IBackgroundCopyJob_AddFile Check for valid filenames and supported protocols
fixme: wininet: InternetLockRequestFile STUB
fixme: file: MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented
fixme: ole: CoInitializeSecurity ((nil),-1,(nil),(nil),2,3,(nil),0,(nil)) - stub!
fixme: qmgr: BITS_IBackgroundCopyJob_GetPriority Not implemented
fixme: qmgr: BITS_IBackgroundCopyJob_SetPriority (0x144990,0x00000001) stub
fixme: qmgr: BITS_IBackgroundCopyJob_GetPriority Not implemented
fixme: qmgr: BITS_IBackgroundCopyJob_AddFile Check for valid filenames and supported protocols
fixme: qmgr: BITS_IBackgroundCopyJob_Cancel Not implemented
fixme: qmgr: BITS_IBackgroundCopyJob_Cancel Not implemented
fixme: wininet: InternetLockRequestFile STUB
fixme: ole: CoInitializeSecurity ((nil),-1,(nil),(nil),2,3,(nil),0,(nil)) - stub!
fixme: qmgr: BITS_IBackgroundCopyJob_GetPriority Not implemented
fixme: qmgr: BITS_IBackgroundCopyJob_SetPriority (0x148940,0x00000002) stub
fixme: qmgr: BITS_IBackgroundCopyJob_GetPriority Not implemented
fixme: qmgr: BITS_IBackgroundCopyJob_AddFile Check for valid filenames and supported protocols
fixme: wininet: InternetLockRequestFile STUB
err: ole: CoGetClassObject class {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} not registered
err: ole: create_server class {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} not registered
fixme: ole: CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err: ole: CoGetClassObject no class object {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} could be created for context 0x15
err: ole: CoGetClassObject class {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} not registered
err: ole: create_server class {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} not registered
fixme: ole: CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err: ole: CoGetClassObject no class object {b5f8350b-0548-48b1-a6ee-88bd00b4a5e7} could be created for context 0x15
fixme: keyboard: X11DRV_MapVirtualKeyEx keyboard layout (nil) is not supported
fixme: file: MoveFileWithProgressW MOVEFILE_WRITE_THROUGH unimplemented


```

 
How do I fix this? I'd really like to have comments and highlights in my PDFs..

---

