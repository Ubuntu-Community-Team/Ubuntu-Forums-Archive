---
title: "Software not Functioning Properly on Wine"
date: 2018-12-01
forum: Wine
---

### Post by flyguy84 on 2018-12-01
Hi Everyone,
I am brand new to Linux and have very limited experience, but I am really liking it so far.  I am running Lubuntu 16.04.5 on an older MSI Netbook, and I am trying to get my professional pilot logbook software to work.  The program is Logbook Pro from NC Software.  I was able to install Logbook Pro and restore my data from a backup file, but I am unable to run any   reports (it just says processing and never does anything)  and my data   from my android app is not syncing either.  Also the summary bar that display totals is not making sense.

I really hope I can get it to work because this is the only thing stopping me from saying goodbye to Windows for good.


This is what I have when I open the program in the LX Terminal:
```
fixme:olepicture:OleLoadPictureEx (0x157d4c4,24950,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x33f844), partially implemented.
fixme:ole:RemUnknown_QueryInterface No interface for iid {00000019-0000-0000-c000-000000000046}
err:winediag:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path. Usually, you can find it in the winbind package of your distribution.
fixme:olepicture:OLEPictureImpl_SaveAsFile (0x14f1e8)->(0x20e1110, 0, (nil)), hacked stub.
fixme:olepicture:OleLoadPictureEx (0x157ebcc,27501,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x33f844), partially implemented.
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:winediag:AUDDRV_GetAudioEndpoint Winepulse is not officially supported by the wine project
fixme:winediag:AUDDRV_GetAudioEndpoint For sound related feedback and support, please visit [http://ubuntuforums.org/showthread.php?t=1960599](http://ubuntuforums.org/showthread.php?t=1960599)
fixme:share:NetShareEnum Stub ((null) 2 0x33e3b8 -1 0x33e3c0 0x33e3b4 (nil))
fixme:share:NetShareEnum Stub ((null) 2 0x33e0b0 -1 0x33e0b8 0x33e0ac (nil))
fixme:share:NetShareEnum Stub ((null) 2 0x33e18c -1 0x33e194 0x33e188 (nil))
fixme:odbc:SQLConfigDataSource (nil) 1 "Microsoft Access Driver (*.mdb)" "DSN=NCSoftware"
fixme:olepicture:OleLoadPictureEx (0x1580c4c,902,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x33f2e0), partially implemented.
err:ole:CoGetClassObject class {00000000-0000-0000-0000-000000000000} not registered
err:ole:CoGetClassObject no class object {00000000-0000-0000-0000-000000000000} could be created for context 0x1
err:ole:CoGetClassObject class {00000000-0000-0000-0000-000000000000} not registered
err:ole:CoGetClassObject no class object {00000000-0000-0000-0000-000000000000} could be created for context 0x1
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x2be16e4), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x2be4a14), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x2be8754), stub!
fixme:ole:OLEFontImpl_IPersistStreamInit_InitNew (0x2bfa3bc), stub!
fixme:olepicture:OLEPictureImpl_SaveAsFile (0x2b16de0)->(0x2be7918, 0, (nil)), hacked stub.
fixme:share:NetShareEnum Stub ((null) 2 0x33db9c -1 0x33dba4 0x33db98 (nil))
fixme:olepicture:OleLoadPictureEx (0x158d46c,902,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x33d5c0), partially implemented.
fixme:olepicture:OLEPictureImpl_SaveAsFile (0x2b58c20)->(0x8b6d588, 0, (nil)), hacked stub.


```

---

