---
title: "Counter Strike 1.6 doesn't start!"
date: 2008-02-22
forum: Wine
---

### Post by saz on 2008-02-22
Hi there!

I've followed this HOWTO [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games") to install steam and counter strike 1.6, this howto has worked for me in the past and i don't see a reason why it's not working now. 

the problem is: counter strike won't start! (yes i have selected OSS on winecfg)

pls see the video of the error (only 600kb):

[http://rapidshare.com/files/94049784/error.ogg.html]("http://rapidshare.com/files/94049784/error.ogg.html")

---

### Post by blackdragon1157 on 2008-02-22
What is the terminal output? 

If your not sure how, run this:
```

wine steam.exe -applaunch 10

```

---

### Post by jmorth on 2008-02-22
I just installed Steam like seven hours or so.

I don't know if this will help, but it might.

I have WINE installed.
I downloaded the old steam .exe that frodon has posted in this thread: [http://ubuntuforums.org/showthread.php?t=502685]("http://ubuntuforums.org/showthread.php?t=502685")

I then right clicked in the exe file and selected "open with WINE". It started installing and then the Steam window should open.  (Make sure you have the tahoma font installed in your WINE c:\windows\fonts folder. Otherwise you won't be able to read anything.)

Steam should try to update itself. JUST LET IT WORK!!!! It seems like it hangs up but after a few minutes, it finishes.

Now after I downloaded and updated my games, I selected counterstrike to play. When I clicked on it, it went to the desktop, but my resolution was wrong. It looked like 800x600. At the bottom of my screen was the task bar and it had counterstrike on it. I clicked on it and a few seconds later it started up.

Remember, since WINE is basically acting as a windows box, it may take a bit longer for things to happen.

Hope this helps.

A little off-topic, I ran around a bit in game and noticed that I was pulling a consistent 70 fps. When I had XP on this SAME computer I was lucky to hit 50 fps.

---

### Post by saz on 2008-02-23
> **blackdragon1157 said:**
> What is the terminal output? 

not a very nice output:

```
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
dir: Z:\home\sa\.PlayOnLinux\wineprefix\Steam\drive_c\Program Files\Steam\bin\ *.mix
dir: Z:\home\sa\.PlayOnLinux\wineprefix\Steam\drive_c\Program Files\Steam\bin\ *.asi
dir: Z:\home\sa\.PlayOnLinux\wineprefix\Steam\drive_c\Program Files\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
fixme:shdocvw:ViewObject_SetAdvise (0x107901e0)->(1 00000002 0x12ae1e8)
fixme:shdocvw:PersistStreamInit_InitNew (0x107901e0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x107901e0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x107901e0)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0xf110028)->(1 00000002 0x12ae250)
fixme:shdocvw:PersistStreamInit_InitNew (0xf110028)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xf110028)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xf110028)->(ffffffff)
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x34c3b4,0x00000000), stub!
fixme:ntdll:server_ioctl_file Unsupported ioctl 90073 (device=9 access=0 func=1c method=3)
fixme:ntdll:server_ioctl_file Unsupported ioctl 90073 (device=9 access=0 func=1c method=3)
fixme:ntdll:server_ioctl_file Unsupported ioctl 90073 (device=9 access=0 func=1c method=3)
fixme:ntdll:server_ioctl_file Unsupported ioctl 90073 (device=9 access=0 func=1c method=3)
fixme:ntdll:server_ioctl_file Unsupported ioctl 90073 (device=9 access=0 func=1c method=3)
fixme:ntdll:server_ioctl_file Unsupported ioctl 90073 (device=9 access=0 func=1c method=3)
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shdocvw:ViewObject_SetAdvise (0x10755690)->(1 00000002 0x12af888)
fixme:shdocvw:PersistStreamInit_InitNew (0x10755690)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x10755690)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x10755690)->(ffffffff)
fixme:iphlpapi:NotifyAddrChange (Handle 0x7a5519c8, overlapped 0x7a5519ac): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x11e0ef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x10755728)->((null) 1 0x34c120 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x10755728)->((null) 25 2 0x34c148 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x10755728)->((null) 26 2 0x34c148 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:shdocvw:ClientSite_GetContainer (0x10755728)->(0x34c194)
fixme:shdocvw:ClOleCommandTarget_Exec (0x10755728)->({000214d1-0000-0000-c000-000000000046} 37 0 0x34c2a8 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x10755958)->(L"" L"" 0 0x34c224)
fixme:mshtml:fix_headers Ignoring User-Agent header
fixme:process:IsWow64Process (0xffffffff 0x3e6e88) stub!
fixme:win:SetLayeredWindowAttributes (0x30098,0x00000000,53,2): stub!
fixme:shdocvw:ClOleCommandTarget_Exec (0x10755728)->((null) 29 2 0x34c0b8 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x10755728)
fixme:shdocvw:ClientSite_GetContainer (0x10755728)->(0x34c068)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x10755728)->(0xb7eb6734)
fixme:shdocvw:ClOleCommandTarget_Exec (0x10755728)->((null) 25 2 0x34bf7c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x10755728)->((null) 26 2 0x34bf7c (nil))
fixme:mshtml:HTMLBodyElement_put_scroll (0x10368130)->(L"no")
fixme:mshtml:HTMLDocument_put_ondragstart (0x107593b8)
fixme:mshtml:HTMLBodyElement_put_scroll (0x10368130)->(L"no")
fixme:mshtml:HTMLBodyElement_put_scroll (0x10368130)->(L"no")
fixme:win:SetLayeredWindowAttributes (0x30098,0x00000000,53,2): stub!
fixme:shdocvw:ClOleCommandTarget_Exec (0x10755728)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x10755728)->((null) 28 2 0x34bf78 (nil))
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:win:SetLayeredWindowAttributes (0x30098,0x00000000,196,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30098,0x00000000,139,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30098,0x00000000,139,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30098,0x00000000,120,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30098,0x00000000,86,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30098,0x00000000,29,2): stub!
fixme:win:SetLayeredWindowAttributes (0x30098,0x00000000,0,2): stub!
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x10755690)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x10755690)
fixme:shdocvw:OleObject_Close (0x10755690)->(1)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x107593b8)->((nil))
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x34f654,0x00000000), stub!
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:mshtml:hidden_proc (0x100ac 49227 0 1)
fixme:shdocvw:ViewObject_SetAdvise (0x1934b8)->(1 00000002 0x3db50c0)
fixme:shdocvw:PersistStreamInit_InitNew (0x1934b8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1934b8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1934b8)->(ffffffff)
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
fixme:shdocvw:ViewObject_SetAdvise (0x10548010)->(1 00000002 0x12af138)
fixme:shdocvw:PersistStreamInit_InitNew (0x10548010)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x10548010)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x10548010)->(ffffffff)
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x11e0ef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x105480a8)->((null) 1 0x349398 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x105480a8)->((null) 25 2 0x3493c0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x105480a8)->((null) 26 2 0x3493c0 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:shdocvw:ClientSite_GetContainer (0x105480a8)->(0x34940c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x105480a8)->({000214d1-0000-0000-c000-000000000046} 37 0 0x349520 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x134530)->(L"" L"" 0 0x34949c)
fixme:mshtml:fix_headers Ignoring User-Agent header
fixme:shdocvw:ClOleCommandTarget_Exec (0x105480a8)->((null) 29 2 0x34c0b8 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x105480a8)
fixme:shdocvw:ClientSite_GetContainer (0x105480a8)->(0x34c068)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x105480a8)->(0xb7eb6734)
fixme:shdocvw:ClOleCommandTarget_Exec (0x105480a8)->((null) 25 2 0x34bf7c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x105480a8)->((null) 26 2 0x34bf7c (nil))
fixme:mshtml:HTMLBodyElement_put_scroll (0x1052fa98)->(L"no")
fixme:mshtml:HTMLDocument_put_ondragstart (0x104fcc50)
fixme:mshtml:HTMLBodyElement_put_scroll (0x1052fa98)->(L"no")
fixme:mshtml:HTMLBodyElement_put_scroll (0x1052fa98)->(L"no")
fixme:mshtml:HTMLBodyElement_put_scroll (0x1052fa98)->(L"no")
fixme:shdocvw:ClOleCommandTarget_Exec (0x105480a8)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x105480a8)->((null) 28 2 0x34bf78 (nil))
fixme:win:SetLayeredWindowAttributes (0x4009a,0x00000000,225,2): stub!
fixme:win:SetLayeredWindowAttributes (0x4009a,0x00000000,225,2): stub!
fixme:win:SetLayeredWindowAttributes (0x4009a,0x00000000,216,2): stub!
fixme:win:SetLayeredWindowAttributes (0x4009a,0x00000000,197,2): stub!
fixme:win:SetLayeredWindowAttributes (0x4009a,0x00000000,144,2): stub!
fixme:win:SetLayeredWindowAttributes (0x4009a,0x00000000,102,2): stub!
fixme:win:SetLayeredWindowAttributes (0x4009a,0x00000000,87,2): stub!
fixme:win:SetLayeredWindowAttributes (0x4009a,0x00000000,83,2): stub!
fixme:win:SetLayeredWindowAttributes (0x4009a,0x00000000,50,2): stub!
fixme:win:SetLayeredWindowAttributes (0x4009a,0x00000000,30,2): stub!
fixme:win:SetLayeredWindowAttributes (0x4009a,0x00000000,16,2): stub!
fixme:win:SetLayeredWindowAttributes (0x4009a,0x00000000,16,2): stub!
fixme:win:SetLayeredWindowAttributes (0x4009a,0x00000000,7,2): stub!
fixme:win:SetLayeredWindowAttributes (0x4009a,0x00000000,0,2): stub!
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x10548010)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x10548010)
fixme:shdocvw:OleObject_Close (0x10548010)->(1)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x104fcc50)->((nil))
Shutting down. . .
3fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set

```

now, something similar is happening to GTA:SA i've just installed, so i guess it's only a CS config, but a Steam/wine config or some OS config...

---

### Post by saz on 2008-02-23
can someone pls help me?

---

### Post by Kopfgeldjaeger on 2008-03-01
I have exactly the same problem!

cheers

---

### Post by naz37 on 2008-03-01
I had a problem a similar problem a while back with source based games(HL2,CSS,Portal) they would get to the loading screen and then crash. I fixed it by enabling ALSA support and disabling OSS.

Hope this will help.

---

### Post by saz on 2008-03-27
managed to get it working, just start CS in D3D (add "-d3d" on game launch, you can add this through steam, just right click on CS, properties, etc)

but i'd really like to play it with opengl... if anybody can, pls help me..

---

### Post by DavidFromCanada on 2008-08-16
This is bugging me too
Half-Life, Blue Shift and Opposing Force work but I can't get Day of Defeat or Counter-Strike to work.

---

