---
title: "Adobe Photoshop CS2 on wine 1.0-rc3"
date: 2008-06-06
forum: Wine
---

### Post by reyhan on 2008-06-06
Hello i want to install Photoshop 9 CS2 but i can't 
this is the Output on the Terminal

```
reyhan@reyhan-desktop:~/Documents/PhotoshopCS2$ wine setup.exe
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
fixme:shdocvw:PersistStorage_InitNew (0x13b3f8)->(0x10013378)
fixme:urlmon:URLMonikerImpl_BindToObject use running object table
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:BindStatusCallback_OnProgress status code 11
fixme:shdocvw:BindStatusCallback_OnProgress status code 14
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d9b7a08, overlapped 0x7d9b79ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x16cef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x13b494)->((null) 1 0x328e6c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13b494)->((null) 25 2 0x328e80 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13b494)->((null) 26 2 0x328e80 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x13b494)->(0x328ebc)
fixme:shdocvw:ClOleCommandTarget_Exec (0x13b494)->({000214d1-0000-0000-c000-000000000046} 37 0 0x328f80 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13b494)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x329010)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:shdocvw:ClOleCommandTarget_Exec (0x13b494)->((null) 29 2 0x32bdd4 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x13b494)
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:shdocvw:ClientSite_GetContainer (0x13b494)->(0x32bb20)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x13b494)->(0xb7e9e6d5)
fixme:shdocvw:ClOleCommandTarget_Exec (0x13b494)->((null) 25 2 0x32ba54 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13b494)->((null) 26 2 0x32ba54 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13b494)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32bd2c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x13b494)->({000214d0-0000-0000-c000-000000000046} 69 0 (nil) 0x32bd2c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x13b494)->((null) 26 2 0x32bdb4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13b494)->((null) 29 2 0x32bdc4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13b494)->({000214d1-0000-0000-c000-000000000046} 103 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13b494)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13b494)->((null) 35 0 (nil) (nil))
fixme:shdocvw:InPlaceFrame_SetStatusText (0x13b494)->(0x7bca27af)
fixme:shdocvw:ClOleCommandTarget_Exec (0x13b494)->((null) 28 2 0x32bd2c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x13b494)->((null) 21 2 (nil) (nil))
fixme:shdocvw:OleObject_Close (0x13b3f8)->(1)
reyhan@reyhan-desktop:~/Documents/PhotoshopCS2$ fixme:sfc:SfcIsKeyProtected ((nil), (null)) stub
fixme:advapi:RegisterEventSourceA ((null),"MsiInstaller"): stub
fixme:advapi:RegisterEventSourceW (L"",L"MsiInstaller"): stub
fixme:advapi:ReportEventA (0xcafe4242,0x0001,0x0000,0x000003f5,(nil),0x0006,0x00000000,0x33e4b0,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0001,0x0000,0x000003f5,(nil),0x0006,0x00000000,0x133280,(nil)): stub
err:eventlog:ReportEventW L"=====================================================\r\nException code: C0000005 ACCESS_VIOLATION\r\nFunction: 0x0\r\n=====================================================\r\n\r\nRegisters:\r\nEAX:00000000  EBX:004BEF2D  ECX:0033E4EC  EDX:00000031  ESI:0033E674  EDI:00000000\r\nCS:EIP:0073:00000000 "...
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L""
err:eventlog:ReportEventW L""
fixme:advapi:DeregisterEventSource (0xcafe4242) stub


```
Can Someone Help me?:(:(

---

