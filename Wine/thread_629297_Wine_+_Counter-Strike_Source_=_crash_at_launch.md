---
title: "Wine + Counter-Strike: Source = crash at launch"
date: 2007-12-02
forum: Wine
---

### Post by flippykid on 2007-12-02
Hello everyone, I know what you´re thinking, ¨but there are already loads of other threads like this!¨ but none of them have helped me in the past so I´m making a new one. Well I installed counter-strike and steam with no problem, I was able to get counter-strike 1.6 to work, with lagtastic results >_<, Anyways When I installed counter-strike source I got a message saying that my driver may have been out of date or something, but I´m guessing that that´s normal, oh and I have a radeon 9000 pro, with no other ristricted drivers... If that´s the one where you have to download from you´re video card distrobuter or something. And well I start up the game, with all my visual extras set to off, and using OSS sound. And I see the backround image, showing up in about the native resolution (600etc) and the loading text in the corner. After about half a minute the game disapears into thin air, leaving my desktop resolution at 600etc. Can someone please help me out, if there is anything I didn´t state, please tell me.

---

### Post by cogadh on 2007-12-02
Post post error output Wine produces in the terminal, it might help with determining a cause.

---

### Post by flippykid on 2007-12-02
How do I do that? Do I just like open terminal before i launch? do i launch through terminal?

---

### Post by cogadh on 2007-12-02
Open a terminal, change directories to Steam's install directory, then run Steam:
```
cd .wine/drive_c/Program\ Files/Steam
wine Steam.exe
```
Copy the output text from the terminal to a post here, make sure you use the forum CODE tags, it will make it easier to read.

---

### Post by flippykid on 2007-12-02
Alright this is what I got when I launched steam, I didn´t launch Counter-Strike yet, but I´m going to do so in a bit.

```
bernard@Bernard:~$ cd .wine/drive_c/Program\ Files/Steam
bernard@Bernard:~/.wine/drive_c/Program Files/Steam$ wine Steam.exe
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
dir: C:\Program Files\Steam\bin\ *.mix
dir: C:\Program Files\Steam\bin\ *.asi
dir: C:\Program Files\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
fixme:shdocvw:ViewObject_SetAdvise (0x1078b0e0)->(1 00000002 0x149d348)
fixme:shdocvw:PersistStreamInit_InitNew (0x1078b0e0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1078b0e0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1078b0e0)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x1078aa50)->(1 00000002 0x149d3b0)
fixme:shdocvw:PersistStreamInit_InitNew (0x1078aa50)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1078aa50)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1078aa50)->(ffffffff)
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,0,2): stub!
fixme:iphlpapi:NotifyAddrChange (Handle 0x72cbb9f8, overlapped 0x72cbb9dc): stub
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1078b174)->((null) 1 0x34bcac (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1078b174)->((null) 25 2 0x34bcc0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1078b174)->((null) 26 2 0x34bcc0 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:shdocvw:ClientSite_GetContainer (0x1078b174)->(0x34bcfc)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1078b174)->({000214d1-0000-0000-c000-000000000046} 37 0 0x34bdb8 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x13754810)->(L"" L"" 0 0x34bdec)
fixme:shdocvw:BindStatusCallback_GetBindInfo (0x13754810)->(0x34bdf0 0x34be00)
fixme:mshtml:fix_headers Ignoring User-Agent header
err:systray:delete_icon invalid tray icon ID specified: 1
fixme:shdocvw:ClOleCommandTarget_Exec (0x1078b174)->((null) 29 2 0x34d590 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1078b174)
fixme:shdocvw:ClientSite_GetContainer (0x1078b174)->(0x34d5b0)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1078b174)->(0xb7e05109)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1078b174)->((null) 25 2 0x34d4e4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1078b174)->((null) 26 2 0x34d4e4 (nil))
fixme:mshtml:HTMLBodyElement_put_scroll (0x129fc3f8)->(L"no")
fixme:mshtml:HTMLDocument_put_ondragstart (0x13754d58)
fixme:mshtml:HTMLBodyElement_put_scroll (0x129fc3f8)->(L"no")
fixme:mshtml:HTMLBodyElement_put_scroll (0x129fc3f8)->(L"no")
fixme:shdocvw:ClOleCommandTarget_Exec (0x1078b174)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1078b174)->((null) 28 2 0x34d458 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1078b174)->((null) 26 2 0x34d570 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1078b174)->((null) 29 2 0x34d580 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1078b174)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1078b174)->((null) 35 0 (nil) (nil))
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1078b174)->(0x7bc9e554)
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,246,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,246,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,47,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,47,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,0,2): stub!
```
O.K I started up counter-strike source from the icon after I launched steam they way you told me to and I got this, and it repeats the last command all the way through to the end about.

```
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x34c1c4,0x00000000), stub!
fixme:shdocvw:ViewObject_SetAdvise (0x1344b698)->(1 00000002 0x14ab708)
fixme:shdocvw:PersistStreamInit_InitNew (0x1344b698)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1344b698)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1344b698)->(ffffffff)
fixme:process:IsWow64Process (0xffffffff 0x3e6e88) stub!
fixme:win:SetLayeredWindowAttributes (0x400a2,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x400a2,0x00000000,168,2): stub!
fixme:win:SetLayeredWindowAttributes (0x400a2,0x00000000,0,2): stub!
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1344b698)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1344b698)
fixme:shdocvw:OleObject_Close (0x1344b698)->(1)
ALSA lib conf.c:3949:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
fixme:win:EnumDisplayDevicesW ((null),0,0x34e1e4,0x00000000), stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:d3d9:D3DPERF_SetOptions (0x1) : stub
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1371a0) Event query: Unimplemented, but pretending to be supported
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1371a0) Event query: Unimplemented, but pretending to be supported
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_cmp (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_low (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_pow (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_mul_high (a)
fixme:dbghelp_dwarf:dwarf2_parse_variable Unsupported form for const value srgb_sub_high (a)
fixme:avifile:AVIFileExit (): stub!
```

---

### Post by flippykid on 2007-12-04
Can anyone at all help me out? please, I really want to get this to work.

---

### Post by Promaster91 on 2007-12-04
This may help if you are using version 1.6.
[http://gentoo-wiki.com/HOWTO_Counter-Strike_1.6_With_WINE](http://gentoo-wiki.com/HOWTO_Counter-Strike_1.6_With_WINE)

---

### Post by daimaru on 2007-12-04
just as it says in the howto on gentoo-wiki 
1. you have a nvidia graphics card....

you dont. so problem!!!

I'm just telling you this because i had the same issue with a ati radeon gto 800 and i could never get it to work without bigtime lag. I envied the people that said well counterstrike works great for me i'm using nvidia. 

so i now have bought a nvidia graphics card and guess what it works perfectly. I can play counterstrike cs hl2 through wine without any lag ( i actually think its faster than on windows ). 

so unless ati releases some great new driver or someone really has hacked his way through this you are better off buying the cheapest nvidia card you can find, instead of using ati.

---

### Post by flippykid on 2007-12-05
I have $22 and like 25 cents -_- I don´t think I will be buying anything soon, and I just lost my job too. There must be another way, plus I can´t spend all my money on something I´m not 100% will work. But thanks for the info, I will look into it further.

---

