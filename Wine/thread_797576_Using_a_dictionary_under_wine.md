---
title: "Using a dictionary under wine"
date: 2008-05-17
forum: Wine
---

### Post by Stefanie on 2008-05-17
I have a Latin-Dutch dictionary on cd-rom. Unfortunately it's built for windows but i tried to install it using wine. install went ok and when i open the application i see the welcome screen (see attachment). in windows xp i just click on the input field (left upper corner of the screen) and type the word i want to look up, but this seems to be impossible under wine... when i click on a link (eg "help"), the screen turns blank.

i think the dictionary is built to use internet explorer, but wine installed gecko the first time i opened it so i thought it would be fine.

any ideas? i already tried switching the winecfg to different windows configurations, but that didn't do the trick.

---

### Post by Stefanie on 2008-05-17
btw i'm using wine 09.46 and i get this when i run the program from terminal:
```
fixme:font:CreateScalableFontResourceA (0,"c:\\windows\\temp\\AUP_LANE\\LaNe.WB\\LANES___.FOT","LANES___.TTF","c:\\windows\\temp\\AUP_LANE\\LaNe.WB\\"): stub
fixme:shdocvw:PersistStreamInit_InitNew (0x12c420)
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -504, flags 0x2!
fixme:shdocvw:navigate_url Unsupported arguments
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x12c4b4)->((null) 1 0x34f220 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12c4b4)->((null) 25 2 0x34f234 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12c4b4)->((null) 26 2 0x34f234 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x12c4b4)->(0x34f270)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12c4b4)->({000214d1-0000-0000-c000-000000000046} 37 0 0x34f32c (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x1465c8)->(L"" L"" 0 0x34f360)
fixme:shdocvw:BindStatusCallback_GetBindInfo (0x1465c8)->(0x34f364 0x34f374)
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -504, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -504, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -514, flags 0x2!
err:ole:ITypeInfo_fnInvoke did not find member id -504, flags 0x2!
fixme:shdocvw:ClOleCommandTarget_Exec (0x12c4b4)->((null) 29 2 0x34f698 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x12c4b4)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:shdocvw:ClientSite_GetContainer (0x12c4b4)->(0x34f6b8)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x12c4b4)->(0xb7eeb109)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12c4b4)->((null) 25 2 0x34f5ec (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12c4b4)->((null) 26 2 0x34f5ec (nil))
fixme:mshtml:HTMLDocument_get_frames (0x147028)->(0x34f344)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x12c49a0)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x1224cb8)
fixme:mshtml:nsChannel_GetOwner default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:nsURI_GetHostPort default action not implemented
fixme:mshtml:nsChannel_SetContentType default action not implemented
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x12cb768)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x1224cb8)
fixme:mshtml:nsChannel_GetOwner default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:nsURI_GetHostPort default action not implemented
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x12cfa50)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x1224cb8)
fixme:mshtml:nsChannel_GetOwner default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:nsURI_GetHostPort default action not implemented
fixme:shdocvw:ClOleCommandTarget_Exec (0x12c4b4)->((null) 26 2 0x34f678 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12c4b4)->((null) 29 2 0x34f688 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12c4b4)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12c4b4)->((null) 35 0 (nil) (nil))
fixme:shdocvw:InPlaceFrame_SetStatusText (0x12c4b4)->(0x7bc9e5b9)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12c4b4)->((null) 28 2 0x34f5f0 (nil))
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2dccd88)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x1224cb8)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2dcb920)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2dd20b8)
fixme:mshtml:nsURI_Equals default action not implemented
fixme:mshtml:nsURI_Equals default action not implemented
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2dea988)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2dd51b8)
fixme:mshtml:nsChannel_GetOwner default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:nsURI_GetHostPort default action not implemented
fixme:mshtml:nsChannel_SetContentType default action not implemented
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2df1728)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2dd51b8)
fixme:mshtml:nsChannel_GetOwner default action not implemented
fixme:mshtml:nsChannel_GetSecurityInfo default action not implemented
fixme:mshtml:nsURI_GetHostPort default action not implemented
fixme:mshtml:nsChannel_SetContentType default action not implemented
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2e03038)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2dd51b8)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2e06450)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2e0b728)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2e07cf0)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2dd51b8)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2e0bdd0)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2e0b8d8)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2e0d158)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2dd51b8)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2e0db68)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2dd51b8)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2e0e8c8)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2dd51b8)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2e0f378)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2dd51b8)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2e0fd30)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2dd51b8)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2e105e8)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2dd51b8)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2e11380)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2dd51b8)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2e12810)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2dd51b8)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2e13208)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2dd51b8)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2e13f20)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2dd51b8)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2e14890)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2dd51b8)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2e151f0)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2dd51b8)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2e15aa8)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2dd51b8)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2e167a8)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2dd51b8)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2e17108)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2dd51b8)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2dc57e8)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2dd51b8)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2e3b1f0)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2e26e58)
fixme:mshtml:nsURI_Equals default action not implemented
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2e4f8b0)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2e26e58)
fixme:mshtml:nsURI_Equals default action not implemented
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2ebede0)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2e26e58)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:mshtml:BSCServiceProvider_QueryService (0x2f82d00)->({79eac9e4-baf9-11ce-8c82-00aa004ba90b} {79eac9e4-baf9-11ce-8c82-00aa004ba90b} 0x2e26e58)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12c4b4)->((null) 21 2 (nil) (nil))
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:mshtml:nsURI_GetOriginCharset default action not implemented
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:mshtml:nsURI_GetOriginCharset default action not implemented
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:mshtml:nsURI_GetOriginCharset default action not implemented
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:mshtml:nsURI_GetOriginCharset default action not implemented
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
fixme:shdocvw:InPlaceActiveObject_TranslateAccelerator (0x12c420)->(0x1290a8)
```

it's a very simple program i think so i hope it will work under wine...

---

### Post by Half-Left on 2008-05-17
You should try the newer version of WINE, some apps dont show or work proper because of no proper MS fonts installed.

---

### Post by happyhamster on 2008-05-17
- Just a wild guess: perhaps the dictionary is stored as html files on the disc. In that case you could perhaps navigate the cd directly with firefox.

- Also, to test if gecko was installed properly, run:

wine iexplore [http://www.winehq.org](http://www.winehq.org)

- It should display the wine home page.

---

### Post by Stefanie on 2008-05-17
thanks. i'm running wine 9.59 now, apparently this is the latest version available for gutsy. i can enter words now, but when i click "search" or hit enter the screen goes blank. 

gecko seems to work fine, the winehq homepage shows up correctly. i checked but i can't navigate the dictionary from the cd.

---

### Post by Stefanie on 2008-05-17
i think the application might be using a custom font, which is included in the folder. how can i install this .ttf font in wine?

---

### Post by Half-Left on 2008-05-17
Put them in ~/.wine/drive_c/windows/Fonts

---

### Post by Stefanie on 2008-05-17
it didn't work, still this blank screen...

---

### Post by Stefanie on 2008-05-17
i found a solution :-) apparently gecko was the problem. i installed ies4linux and i copied the application folder from .wine/program files to .ies4linux/program files. then i was able to browse the folder in IE6 and i could open the application in IE6 itself. 

i guess it's not the most practical solution, but at least it works.

is this a bug in gecko?

---

