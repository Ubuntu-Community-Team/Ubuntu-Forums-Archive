---
title: "Initialization failed for WineD3DDevice"
date: 2008-02-13
forum: Wine
---

### Post by Alpha7 on 2008-02-13
So I have just install Ubuntu 7.10 as well as the latest wine 9.55 (note I've also tried all of this with 9.46, and v9.54 and get same results)

I'm trying to start CSS or HL2, other games so far are working decently, I have a lot of other questions on stuff but I want to focus on this and see if I can get Source games working. 

I have installed DirectX9c and everything appears to be fine as the CSS splash screen comes up for a second then crashes, the last thing that comes up in the console is 
"Initialization failed for WineD3DDevice 0x18e018" and I've looked everywhere for a solution to this one and found nothing of use...

I was hoping there is a solution. 

My system is an AMD 64 X2 5200 Process (not running 64bit)
2GB RAM
ATI Radeon X1950 (with Linux ATI Drivers from ATI.com with the proprietary drivers in use) DirectDraw and Direct3D tests pass in dxdiag

If any other info is needed please ask.
Any help would be apreciated

the output from terminal from the moment I start Steam
> wine Steam.exe
fixme:spoolsv:serv_main (0 (nil))
err:advapi:service_get_status service protocol error - failed to read pipe r = 0  count = 0!
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
dir: C:\Program Files\Steam\bin\ *.mix
dir: C:\Program Files\Steam\bin\ *.asi
dir: C:\Program Files\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
fixme:shdocvw:ViewObject_SetAdvise (0x10d40318)->(1 00000002 0x14ce130)
fixme:shdocvw:PersistStreamInit_InitNew (0x10d40318)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x10d40318)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x10d40318)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x10ba02f0)->(1 00000002 0x14ce198)
fixme:shdocvw:PersistStreamInit_InitNew (0x10ba02f0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x10ba02f0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x10ba02f0)->(ffffffff)
fixme:win:SetLayeredWindowAttributes (0x2002a,0x00000000,0,2): stub!
fixme:iphlpapi:NotifyAddrChange (Handle 0x7aeed9f8, overlapped 0x7aeed9dc): stub
fixme:system:SetProcessDPIAware stub!
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x10d403b0)->((null) 1 0x34b854 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x10d403b0)->((null) 25 2 0x34b868 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x10d403b0)->((null) 26 2 0x34b868 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:shdocvw:ClientSite_GetContainer (0x10d403b0)->(0x34b8a4)
fixme:shdocvw:ClOleCommandTarget_Exec (0x10d403b0)->({000214d1-0000-0000-c000-000000000046} 37 0 0x34b968 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x10ed0218)->(L"" L"" 0 0x34b9a0)
fixme:mshtml:fix_headers Ignoring User-Agent header
fixme:shdocvw:ClOleCommandTarget_Exec (0x10d403b0)->((null) 29 2 0x34d548 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x10d403b0)
fixme:shdocvw:ClientSite_GetContainer (0x10d403b0)->(0x34d518)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x10d403b0)->(0xb7eb016d)
fixme:shdocvw:ClOleCommandTarget_Exec (0x10d403b0)->((null) 25 2 0x34d44c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x10d403b0)->((null) 26 2 0x34d44c (nil))
fixme:mshtml:HTMLBodyElement_put_scroll (0x18f9e8)->(L"no")
fixme:mshtml:HTMLDocument_put_ondragstart (0x10ed5c60)
fixme:mshtml:HTMLBodyElement_put_scroll (0x18f9e8)->(L"no")
fixme:mshtml:HTMLBodyElement_put_scroll (0x18f9e8)->(L"no")
fixme:mshtml:HTMLBodyElement_put_scroll (0x18f9e8)->(L"no")
fixme:shdocvw:ClOleCommandTarget_Exec (0x10d403b0)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x10d403b0)->((null) 28 2 0x34d410 (nil))
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:ntdll:RtlpWaitForCriticalSection section 0xa39678 "?" wait timed out in thread 0034, blocked by 0032, retrying (60 sec)
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x34cc1c,0x00000000), stub!
fixme:shdocvw:ViewObject_SetAdvise (0x10ab37f0)->(1 00000002 0x14da260)
fixme:shdocvw:PersistStreamInit_InitNew (0x10ab37f0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x10ab37f0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x10ab37f0)->(ffffffff)
fixme:process:IsWow64Process (0xffffffff 0x3e7e88) stub!
fixme:win:SetLayeredWindowAttributes (0x200ac,0x00000000,210,2): stub!
fixme:win:SetLayeredWindowAttributes (0x200ac,0x00000000,210,2): stub!
err:ntdll:RtlpWaitForCriticalSection section 0xf57f810 "?" wait timed out in thread 003e, blocked by 0032, retrying (60 sec)
fixme:win:SetLayeredWindowAttributes (0x200ac,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002a,0x00000000,0,2): stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34e1e4,0x00000000), stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:win:SetLayeredWindowAttributes (0x200ac,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x200ac,0x00000000,0,2): stub!
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x10ab37f0)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x10ab37f0)
fixme:shdocvw:OleObject_Close (0x10ab37f0)->(1)
fixme:d3d9:D3DPERF_SetOptions (0x1) : stub
err:wgl:X11DRV_SetPixelFormat Invalid iPixelFormat: 2
err:wgl:X11DRV_GetPixelFormat Unable to find a WineGLPixelFormat for iPixelFormat=0
err:d3d:CreateContext SetPixelFormat failed on HDC=0x3dc for iPixelFormat=2
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create a new context
fixme:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain (0x13f6f8) Something's still holding the front buffer
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x13f6d0) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x13b760) D3D Initialization failed for WineD3DDevice 0x13f6f8
err:wgl:X11DRV_SetPixelFormat Invalid iPixelFormat: 2
err:wgl:X11DRV_GetPixelFormat Unable to find a WineGLPixelFormat for iPixelFormat=0
err:d3d:CreateContext SetPixelFormat failed on HDC=0x3dc for iPixelFormat=2
err:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain Failed to create a new context
fixme:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain (0x18e018) Something's still holding the front buffer
fixme:d3d9:IDirect3DDevice9Impl_CreateAdditionalSwapChain (0x18dde8) call to IWineD3DDevice_CreateAdditionalSwapChain failed
fixme:d3d9:IDirect3D9Impl_CreateDevice (0x13b760) D3D Initialization failed for WineD3DDevice 0x18e018


---

### Post by Alpha7 on 2008-02-14
Come on, I've seen this error all over, someone has to know something about it.

Any help at all or suggestions

Does this point towards a video card issue or something directly relating to wine?

---

