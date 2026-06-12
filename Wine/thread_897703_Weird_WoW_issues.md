---
title: "Weird WoW issues"
date: 2008-08-22
forum: Wine
---

### Post by eternal_sage on 2008-08-22
okay. some what a newb still, i've been tinkering with Ubuntu all summer, and finally got around to putting it on my beast of a desktop that is my gaming and work rig (i do 3D, not that it matters). i had installed WoW on my wife's laptop (she also switched to Ubuntu, as Vista sucks) but it really couldn't handle it. it ran, but was somewhat slower and clunkier (mostly due to wifi troubles, as it worked better with a hard connection). so i tried to install it on the gaming rig for her using the same guide (over in the wiki) and got totally different results. from the terminal i got the following:

```

env WINEPREFIX="/home/jason/.wine" wine "C:\Program Files\World of Warcraft\Launcher.exe"
fixme:shdocvw:PersistStreamInit_Load (0x174620)->(0x32e328)
fixme:shdocvw:OleControl_FreezeEvents (0x174620)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x174620)->(0)
fixme:shell:IShellLinkA_fnGetPath (0x174bb0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x174bb0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x174b90): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x174b90): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x174f28): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x174f28): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x174b90): WIN32_FIND_DATA is not yet filled.
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d7cea08, overlapped 0x7d7ce9ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x12eef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1746bc)->((null) 1 0x32bcf4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1746bc)->((null) 25 2 0x32bd08 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1746bc)->((null) 26 2 0x32bd08 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x1746bc)->(0x32bd44)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1746bc)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32be08 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x174b90)->(L"" L"" 0 0x32be40)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1746bc)->((null) 29 2 0x32ea0c (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1746bc)
fixme:shdocvw:ClientSite_GetContainer (0x1746bc)->(0x32e84c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1746bc)->(0xb7e3f6d1)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1746bc)->((null) 25 2 0x32e780 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1746bc)->((null) 26 2 0x32e780 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1746bc)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1746bc)->((null) 28 2 0x32e9ac (nil))
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x174620)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x18d838)->((nil))
fixme:shdocvw:OleObject_Close (0x174620)->(1)
fixme:shell:DllCanUnloadNow stub
fixme:msimtf:DllCanUnloadNow ()
jason@Tycho:~$ fixme:advapi:SetSecurityInfo stub
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
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec94,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f298,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f3fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f144,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:win:EnumDisplayDevicesW ((null),0,0x33f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f144,0x00000000), stub!
failed to open C:/Program Files/World of Warcraft/Interface/AddOns
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:ActivateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer @ context.c / 1077
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexImage2D @ surface.c / 340
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexImage2D @ surface.c / 340
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexImage2D @ surface.c / 340
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexImage2D @ surface.c / 340
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexImage2D @ surface.c / 340
fixme:d3d_surface:surface_allocate_surface >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexImage2D @ surface.c / 340
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set


```


which is visually accompanied by a virtual desktop opening (good), the intro movie starting and playing through (also good) then when it tries to go to the main menu, i get an error and it dies. i'm not entirely sure what it means. its not an issue that was otherwise covered on the wiki troubleshooting page or anything, and i tried installing the .dll files.

and for the record, this is my setup:

Ubuntu 8.04.1 ix86
Intel Dual-Core 2 Quad 2.4 gHz
NVidia GeForce 8800 GT 512 MB
2 GB of DDR2 RAM

i am using the NVidia driver from the repository (it seems to be otherwise working this time, although last time i tried Ubuntu on this machine it threw up, don't know why)

---

