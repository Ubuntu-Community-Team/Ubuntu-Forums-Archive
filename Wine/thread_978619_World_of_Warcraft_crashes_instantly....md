---
title: "World of Warcraft crashes instantly..."
date: 2008-11-11
forum: Wine
---

### Post by Neurasthenic on 2008-11-11
Hello,
I'm running Ubuntu 8.10, 64bit version. I'm on a laptop with an Nvidia 8600. I have the newest version of Wine. I installed World of Warcraft and all the patches without a hitch - but the game crashes instantly when I try to run it. The screen resolution changes, then everything gets scrambled and I get an error that the program referenced memory that could not be "read". Here's the end of the output in my terminal as the error occurs:

fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10056 84 0 2b203af)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10056 20 10056 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10054 20 10056 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x1004c 20 10056 2000001)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10056 200 0 18a01a5)
fixme:msimtf:ActiveIMMApp_OnDefWindowProc Stub (0x10048 1c 0 0)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x138ce0)
fixme:msimtf:ActiveIMMApp_Deactivate Stub
fixme:mshtml:HlinkTarget_SetBrowseContext (0x152298)->((nil))
fixme:shdocvw:OleObject_Close (0x138ce0)->(1)
fixme:shell:DllCanUnloadNow stub
fixme:msimtf:DllCanUnloadNow ()
nick@nick-laptop:~$ fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\expansion.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x3aedbc,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x3aecac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af2ac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af408,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af59c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af018,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af150,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:getColorBits Unsupported format: WINED3DFMT_R32F
fixme:win:EnumDisplayDevicesW ((null),0,0x3af018,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af150,0x00000000), stub!
failed to open C:/Program Files/World of Warcraft/Interface/AddOns
fixme:win:EnumDisplayDevicesW ((null),0,0x3adf1c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3adf44,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set






I keep seeing people say that I need to edit Config.wtf to switch to OpenGL... But Config.wtf doesn't even exist in my WoW directory, I'm assuming because I haven't been able to actually launch the game yet. If you need any more details let me know.

---

### Post by Neurasthenic on 2008-11-11
Sorry, I didn't realize I had replied earlier to a thread about the same thing. But I could really use some help on this, I don't understand what could be wrong after following every walkthrough I could find. Not being able to play the one PC game I ever play these days could be a deal breaker for Ubuntu and I.

---

### Post by Neurasthenic on 2008-11-11
Nevermind, I guess I didn't search as well as I thought I did. 

I read in another thread that one guy had to create his own Config.wtf to add the OpenGL line - I tried that and now it seems to be working. Of course, after all this, most of the servers are down.:mad:

---

