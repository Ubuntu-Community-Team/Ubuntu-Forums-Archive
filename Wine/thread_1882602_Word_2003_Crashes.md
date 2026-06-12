---
title: "Word 2003 Crashes"
date: 2011-11-17
forum: Wine
---

### Post by jonhall on 2011-11-17
We are running Microsoft Word 2003 in Wine 1.3.28.  The only DLL overrides in effect are riched20.dll and gdiplus.dll.  This setup worked reasonably well for some time (with the usual minor issues), but now Microsoft Word crashes whenever we open a Word document.  Word opens successfully, and the file opens successfully, but Word immediately freezes for about 10 seconds and then crashes. I've included the error output from wine below.  Does anyone have any idea why this might be happening, and what could be done to fix it?
(By the way, we are using Word out of necessity, not because we like it. We use LibreOffice for almost everything except a few .docs where it has serious problems with the formatting.)

Any help would be greatly appreciated!
fixme:ole:CoInitializeSecurity (0x413ea8,-1,(nil),(nil),1,3,(nil),72,(nil)) - stub!
err:ole:CoGetClassObject class {24e669e1-e90f-4595-a012-b0fd3ccc5c5a} not registered
err:ole:CoGetClassObject no class object {24e669e1-e90f-4595-a012-b0fd3ccc5c5a} could be created for context 0x1
fixme:storage:Storage_ConstructTransacted Unimplemented flags 110022
fixme:storage:create_storagefile Storage share mode not implemented.
fixme:psdrv:PSDRV_DeviceCapabilities DC_BINADJUST: stub.
fixme:psdrv:PSDRV_DeviceCapabilities DC_BINADJUST: stub.
fixme:psdrv:PSDRV_DeviceCapabilities DC_BINADJUST: stub.
fixme:psdrv:PSDRV_ExtEscape QUERYESCSUPPORT(25) - not supported.
fixme:psdrv:PSDRV_DeviceCapabilities DC_BINADJUST: stub.
fixme:psdrv:PSDRV_DeviceCapabilities DC_BINADJUST: stub.
fixme:psdrv:PSDRV_DeviceCapabilities DC_BINADJUST: stub.
fixme:msctf:ThreadMgrSource_AdviseSink (0x1d9660) Unhandled Sink: {6f77c993-d2b1-446e-853e-5912efc8a286}
fixme:msctf:TextStoreACPSink_OnLayoutChange STUB:(0xb9da98)
fixme:msctf:TextStoreACPSink_OnLayoutChange STUB:(0xb9da98)
fixme:msctf:TextStoreACPSink_OnLayoutChange STUB:(0xb9da98)
fixme:msctf:TextStoreACPSink_OnLockGranted OnLockGranted called for something other than an EditSession
fixme:msctf:TextStoreACPSink_OnLayoutChange STUB:(0xb9da98)
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 8 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
fixme:advapi:GetCurrentHwProfileW (0x32c234)
fixme:msctf:TextStoreACPSink_OnStartEditTransaction STUB:(0xb9da98)
fixme:shell:SHGetFileInfoW SHGFI_OVERLAYINDEX unhandled
fixme:msctf:TextStoreACPSink_OnEndEditTransaction STUB:(0xb9da98)
fixme:shell:SHGetFileInfoW SHGFI_OVERLAYINDEX unhandled
fixme:shell:IShellView_fnSaveViewState (0xc590c0) stub
fixme:shell:SHGetFileInfoW SHGFI_OVERLAYINDEX unhandled
fixme:shell:IShellView_fnSaveViewState (0x14b480) stub
fixme:shell:SHGetFileInfoW SHGFI_OVERLAYINDEX unhandled
fixme:shell:IShellView_fnSaveViewState (0xc641f0) stub
fixme:shell:SHGetFileInfoW SHGFI_OVERLAYINDEX unhandled
fixme:shell:IShellView_fnSaveViewState (0xc679e8) stub
fixme:shell:IShellView_fnSaveViewState (0xc89f18) stub
fixme:msctf:TextStoreACPSink_OnStartEditTransaction STUB:(0xb9da98)
fixme:msctf:TextStoreACPSink_OnLayoutChange STUB:(0xc89c80)
fixme:msctf:TextStoreACPSink_OnLayoutChange STUB:(0xc89c80)
fixme:msctf:TextStoreACPSink_OnLayoutChange STUB:(0xc89c80)
fixme:msctf:TextStoreACPSink_OnLockGranted OnLockGranted called for something other than an EditSession
fixme:msctf:TextStoreACPSink_OnEndEditTransaction STUB:(0xb9da98)
fixme:msctf:TextStoreACPSink_OnStartEditTransaction STUB:(0xc89c80)
fixme:msctf:TextStoreACPSink_OnLayoutChange STUB:(0xc89c80)
fixme:msctf:TextStoreACPSink_OnStartEditTransaction STUB:(0xb9da98)
fixme:msctf:TextStoreACPSink_OnEndEditTransaction STUB:(0xc89c80)
fixme:msctf:TextStoreACPSink_OnEndEditTransaction STUB:(0xb9da98)
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7ce75ee0
err:seh:setup_exception_record nested exception on signal stack in thread 0015 eip 7dc7a0a9 esp 7ffd7830 stack 0x562000-0x660000

---

