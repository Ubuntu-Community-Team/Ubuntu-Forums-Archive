---
title: "Steam apps have no sound"
date: 2008-03-15
forum: Wine
---

### Post by Joseph_Schafer on 2008-03-15
I have read the ones about playing the MP3 and they worked for me.... for a while. No matter what I do, with winecfg, aoss, virtual desktop, mp3, or anything, the games wont work with sound. I found if I did a cd into Steam/steamapps/common and did demos that didnt start steam first, those worked. I got all that steam said the whole time it ran, till I quit the game.

```
DbgPrint says: Oreans x32 driver loaded in memory (v1.50)
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
dir: C:\Program Files\Steam\bin\ *.mix
dir: C:\Program Files\Steam\bin\ *.asi
dir: C:\Program Files\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
fixme:shdocvw:ViewObject_SetAdvise (0x103502e0)->(1 00000002 0x14fe6d8)
fixme:shdocvw:PersistStreamInit_InitNew (0x103502e0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x103502e0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x103502e0)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x109180c0)->(1 00000002 0x14fe740)
fixme:shdocvw:PersistStreamInit_InitNew (0x109180c0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x109180c0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x109180c0)->(ffffffff)
fixme:win:SetLayeredWindowAttributes (0x2002a,0x00000000,0,2): stub!
fixme:mshtml:nsIOService_QueryInterface ({986c11d0-f340-11d4-9075-0010a4e73d9a} 0x339b8c)
fixme:mshtml:nsIOService_QueryInterface ({9cc0c2e0-f769-4f14-8cd6-2d2d40466f6c} 0x339b6c)
fixme:mshtml:nsIOService_QueryInterface ({bed52030-bca6-11d2-ba79-00805f8a5dd7} 0x339b08)
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1035037c)->((null) 1 0x33a720 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1035037c)->((null) 25 2 0x33a748 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1035037c)->((null) 26 2 0x33a748 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:shdocvw:ClientSite_GetContainer (0x1035037c)->(0x33a794)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1035037c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33a8a8 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x10910290)->(L"" L"" 0 0x33a824)
fixme:mshtml:fix_headers Ignoring User-Agent header
fixme:shdocvw:ClOleCommandTarget_Exec (0x1035037c)->((null) 29 2 0x33c0b8 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1035037c)
fixme:shdocvw:ClientSite_GetContainer (0x1035037c)->(0x33c068)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1035037c)->(0xb7df3b74)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1035037c)->((null) 25 2 0x33bf7c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1035037c)->((null) 26 2 0x33bf7c (nil))
fixme:mshtml:HTMLBodyElement_put_scroll (0x104b2308)->(L"no")
fixme:mshtml:HTMLDocument_put_ondragstart (0x108da1b0)
fixme:mshtml:HTMLBodyElement_put_scroll (0x104b2308)->(L"no")
fixme:mshtml:HTMLBodyElement_put_scroll (0x104b2308)->(L"no")
fixme:mshtml:HTMLBodyElement_put_scroll (0x104b2308)->(L"no")
fixme:shdocvw:ClOleCommandTarget_Exec (0x1035037c)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1035037c)->((null) 28 2 0x33bf78 (nil))
fixme:shell:SHGetFileInfoW set icon to shell size, stub
fixme:shell:SHGetFileInfoW set icon to shell size, stub
fixme:shell:SHGetFileInfoW set icon to shell size, stub
fixme:bidi:mirror stub: mirroring of characters not yet implemented
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x33cb0c,0x00000000), stub!
fixme:shdocvw:ViewObject_SetAdvise (0xfe375d0)->(1 00000002 0x14f80f0)
fixme:shdocvw:PersistStreamInit_InitNew (0xfe375d0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xfe375d0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xfe375d0)->(ffffffff)
fixme:process:IsWow64Process (0xffffffff 0x3d6e88) stub!
fixme:win:SetLayeredWindowAttributes (0x300a4,0x00000000,237,2): stub!
fixme:win:SetLayeredWindowAttributes (0x300a4,0x00000000,237,2): stub!
fixme:win:SetLayeredWindowAttributes (0x300a4,0x00000000,38,2): stub!
fixme:win:SetLayeredWindowAttributes (0x300a4,0x00000000,0,2): stub!
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0xfe375d0)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0xfe375d0)
fixme:shdocvw:OleObject_Close (0xfe375d0)->(1)
fixme:win:EnumDisplayDevicesW ((null),0,0xb2dcf8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0xb2e0b8,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x143ea8) : stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0xb2e4a4,0xb2e4a0): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0xb2e4a4,0xb2e4a0): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0xb2e4a4,0xb2e4a0): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0xb2e4a4,0xb2e4a0): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0xb2e4a4,0xb2e4a0): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0xb2e4a4,0xb2e4a0): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0xb2e4a4,0xb2e4a0): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0xb2e4a4,0xb2e4a0): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0xb2e4a4,0xb2e4a0): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0xb2e4a4,0xb2e4a0): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0xb2b56c,0xb2b568): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0xb2b020,0xb2b01c): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0xb2b020,0xb2b01c): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0xb2b020,0xb2b01c): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0xb2b020,0xb2b01c): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0xb2b020,0xb2b01c): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0xb2b020,0xb2b01c): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0xb2b020,0xb2b01c): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0xb2b020,0xb2b01c): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0xb2b078,0xb2b074): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0xb2b078,0xb2b074): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0xb2b078,0xb2b074): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0xb2b56c,0xb2b568): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0xb2e390,0xb2e38c): stub
fixme:process:GetProcessWorkingSetSize (0xffffffff,0xb2e390,0xb2e38c): stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x143ea8) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x143ea8) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x143ea8) : stub
Shutting down. . .
3fixme:win:SetLayeredWindowAttributes (0x2002a,0x00000000,0,2): stub!
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set

``` 

Just wondering if anyone knew.
I run alsa in the main thing, but my speakers have trouble, with the sound Icon I cant drag down the bar, it will say muted sound but nothing will happen.
I just bought a game in steam and now it wont work.

Anyone have an idea?

---

### Post by Joseph_Schafer on 2008-03-15
O ya, I also have wine 0.9.57

Steam works for my bro, with sound, but not for me. (hes also on ubuntu)

---

### Post by Joseph_Schafer on 2008-03-16
it just worked 1nce with the mp3.... and after I closed it it wouldnt work again. help??

---

### Post by Joseph_Schafer on 2008-03-19
I think I figured this out.... I have to play TWO mp3s at 1nce, and it works. Its funkey, but is there any way I could edit it so i didnt have to do this each time? Please HELP!!!!!!!

---

