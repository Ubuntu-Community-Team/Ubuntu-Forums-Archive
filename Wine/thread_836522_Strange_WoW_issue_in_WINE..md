---
title: "Strange WoW issue in WINE."
date: 2008-06-21
forum: Wine
---

### Post by rocadellor on 2008-06-21
I recently reformatted my HDD with Ubuntu. Changed my life. I'm so glad to be free of Windows. My only negative experience so far has been compatibility with the applications i was accustomed to using. WINE has been very useful in this area, but the one thing I can't figure out is WoW.

I've read hundreds of threads about my current problem in the last two days, but none addressed my problem specifically.

What I did first:

Installation - I never bought the original WoW discs. I simply downloaded the WoWInstaller.exe paid for my account activation through blizzard, and installed the game from the download. I did, however purchase the Burning Crusade in store. I installed both of these games last night, on my laptop. 

The problem - Whether I start WoW from the Applications menu, the terminal, or selecting the launcher file itself; it opens in WINE, shows the cinematic, and at the end of the cinematic, a noise like a thud sounds, and then it all shuts down. Rinse and repeat. I'm at a loss.

Please reply if you can help in any way, also, let me know if you need more information from me.

---

### Post by rocadellor on 2008-06-21
Here is the error data the Terminal spits out when I try to run WoW.

```
william@william-laptop:~$ wine "C:\Program Files\World of Warcraft\Launcher.exe"
fixme:shdocvw:PersistStreamInit_Load (0x12f660)->(0x32e328)
fixme:shdocvw:OleControl_FreezeEvents (0x12f660)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x12f660)->(0)
fixme:shell:IShellLinkA_fnGetPath (0x12fc10): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x12fbf0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x12fbf0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x130568): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x130568): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x130568): WIN32_FIND_DATA is not yet filled.
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d8e3a08, overlapped 0x7d8e39ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x12eef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x12f6fc)->((null) 1 0x32bcf4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12f6fc)->((null) 25 2 0x32bd08 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12f6fc)->((null) 26 2 0x32bd08 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x12f6fc)->(0x32bd44)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12f6fc)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32be08 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x130568)->(L"" L"" 0 0x32be40)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12f6fc)->((null) 29 2 0x32ea0c (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x12f6fc)
fixme:shdocvw:ClientSite_GetContainer (0x12f6fc)->(0x32e84c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x12f6fc)->(0xb7ebd6d1)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12f6fc)->((null) 25 2 0x32e780 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12f6fc)->((null) 26 2 0x32e780 (nil))
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:shdocvw:ClOleCommandTarget_Exec (0x12f6fc)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12f6fc)->((null) 28 2 0x32e9ac (nil))
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x12f660)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x148930)->((nil))
fixme:shdocvw:OleObject_Close (0x12f660)->(1)
fixme:shell:DllCanUnloadNow stub
fixme:msimtf:DllCanUnloadNow ()
william@william-laptop:~$ fixme:advapi:SetSecurityInfo stub
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\common.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x33eda4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec94,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f298,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f3fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f144,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x132af8) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x134290) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x33f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f144,0x00000000), stub!
failed to open C:/Program Files/World of Warcraft/Interface/AddOns
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB

william@william-laptop:~$ Mesa 7.0.3-rc2 implementation error: i915_program_error: Exceeded max nr indirect texture lookups
Please report at bugzilla.freedesktop.org
DRM_I830_CMDBUFFER: -22

```

---

### Post by hikaricore on 2008-06-22
Your problem appears to be your intel video chipset (referenced by i915 in only error you actually posted (the end part).

Have you made sure your drivers are installed properly, direct rendering is enabled?

Also are you running in OpenGL or DX mode?

---

### Post by Hairy_Palms on 2008-06-22
also you may well want torun it with the -opengl switch so
> wine "C:\Program Files\World of Warcraft\Launcher.exe" -opengl 

---

### Post by rocadellor on 2008-06-22
> **hikaricore said:**
> Your problem appears to be your intel video chipset (referenced by i915 in only error you actually posted (the end part).

Have you made sure your drivers are installed properly, direct rendering is enabled?

Also are you running in OpenGL or DX mode?

I'm not sure how to make sure my drivers are installed properly (in Ubuntu). Or how to find which drivers i need. And I believe I'm running in OpenGL, I assume..how would I check?

---

### Post by Hairy_Palms on 2008-06-22
to run in opengl mode see my post above

---

