---
title: "Condition Zero with wine"
date: 2007-12-24
forum: Wine
---

### Post by bobbyg on 2007-12-24
Umm. I am having a problem using Condition Zero with Wine. When I launch game from Steam the virtual desktop shrinks to minimum resolution and the game closes. The window stays at minimum resolution.

Anyone know what is going on?

P.S I am new to linux

---

### Post by compiledkernel on 2007-12-24
Try this steam howto. 

[http://gaming.gwos.org/doku.php/wine:steam](http://gaming.gwos.org/doku.php/wine:steam)

---

### Post by bobbyg on 2007-12-24
I followed that tutorial, and I am now in the process of downloading/installing condition zero.
However I did get that 26% error on the initial and then it restarted automatically and finished. Hopefully thats ok. And throughout the Installation of Steam this is the log that printed on in the terminal. I don't know if this is normal or not

```

fixme:exec:SHELL_execute flags ignored: 0x00000500
rob@rob-desktop:~/Desktop$ fixme:advapi:LookupAccountNameW (null) L"rob" (nil) 0x34f7fc (nil) 0x34f800 0x34f7f4 - stub
fixme:advapi:LookupAccountNameW (null) L"rob" 0x13d500 0x34f7fc 0x141c88 0x34f800 0x34f7f4 - stub
fixme:msi:ControlEvent_SpawnWaitDialog Doing Nothing
fixme:msi:ACTION_HandleStandardAction unhandled standard action L"SetODBCFolders"
fixme:msi:msi_unimplemented_action_stub RemoveRegistryValues -> 2 ignored L"RemoveRegistry" table values
fixme:msi:msi_unimplemented_action_stub RemoveShortcuts -> 3 ignored L"Shortcut" table values
fixme:msi:msi_unimplemented_action_stub RemoveFolders -> 1 ignored L"CreateFolder" table values
fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, advertised shortcut
fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, advertised shortcut
fixme:msi:ITERATE_CreateShortcuts poorly handled shortcut format, advertised shortcut
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:shell:DllCanUnloadNow stub
fixme:advapi:SetEntriesInAclA 1 0x34fe68 (nil) 0x34fe60
fixme:advapi:SetNamedSecurityInfoW L"c:\\Program Files\\Steam" 1 4 (nil) (nil) (nil) (nil)
fixme:advapi:SetEntriesInAclA 1 0x34fe68 (nil) 0x34fe60
fixme:advapi:SetNamedSecurityInfoW L"MACHINE\\SOFTWARE\\Valve\\Steam" 4 4 (nil) (nil) (nil) (nil)
fixme:shell:DllCanUnloadNow stub
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
fixme:shdocvw:ViewObject_SetAdvise (0x1d23a8)->(1 00000002 0x1342330)
fixme:shdocvw:PersistStreamInit_InitNew (0x1d23a8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1d23a8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1d23a8)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x1d3078)->(1 00000002 0x1342370)
fixme:shdocvw:PersistStreamInit_InitNew (0x1d3078)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1d3078)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1d3078)->(ffffffff)
fixme:win:SetLayeredWindowAttributes (0x70076,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x70076,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x70076,0x00000000,22,2): stub!
fixme:win:SetLayeredWindowAttributes (0x70076,0x00000000,22,2): stub!
fixme:win:SetLayeredWindowAttributes (0x70076,0x00000000,0,2): stub!
fixme:shdocvw:ViewObject_SetAdvise (0x10c42888)->(1 00000002 0x134db38)
fixme:shdocvw:PersistStreamInit_InitNew (0x10c42888)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x10c42888)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x10c42888)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x10c434f0)->(1 00000002 0x134dba0)
fixme:shdocvw:PersistStreamInit_InitNew (0x10c434f0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x10c434f0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x10c434f0)->(ffffffff)
fixme:win:EnumDisplayDevicesW ((null),0,0x34c268,0x00000000), stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x200aa,0x00000000,0,2): stub!
err:systray:delete_icon invalid tray icon ID specified: 1
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,228,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,224,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,220,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,218,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,216,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,205,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,203,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,201,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,199,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,198,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,196,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,195,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,191,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,186,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,178,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,162,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,148,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,132,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,118,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,104,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,89,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,87,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,84,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,79,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,77,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,64,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,61,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,58,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,57,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,55,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,53,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,51,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,36,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,22,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,6,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100ae,0x00000000,3,2): stub!
fixme:win:SetLayeredWindowAttributes (0x200aa,0x00000000,217,2): stub!
fixme:win:SetLayeredWindowAttributes (0x200aa,0x00000000,217,2): stub!
fixme:win:SetLayeredWindowAttributes (0x200aa,0x00000000,206,2): stub!
fixme:win:SetLayeredWindowAttributes (0x200aa,0x00000000,206,2): stub!
fixme:win:SetLayeredWindowAttributes (0x200aa,0x00000000,188,2): stub!
fixme:win:SetLayeredWindowAttributes (0x200aa,0x00000000,140,2): stub!
fixme:win:SetLayeredWindowAttributes (0x200aa,0x00000000,87,2): stub!
fixme:win:SetLayeredWindowAttributes (0x200aa,0x00000000,30,2): stub!
fixme:win:SetLayeredWindowAttributes (0x200aa,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20066,0x00000000,2,2): stub!
fixme:win:SetLayeredWindowAttributes (0x20066,0x00000000,2,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2004e,0x00000000,36,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2004e,0x00000000,36,2): stub!
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x34cbd4,0x00000000), stub!
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shell:DllCanUnloadNow stub

```

Again. Thanks for helping.

---

### Post by bobbyg on 2007-12-24
Well I tried to start Condition Zero again. and it did the same thing. And when it does load up the sound is choppy. But the audio is set for ALSA. Here is the code kicked out during the client load

```

fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:shdocvw:ClientSite_GetContainer (0x12c51548)->(0x34b9a4)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12c51548)->({000214d1-0000-0000-c000-000000000046} 37 0 0x34ba70 (nil))
fixme:shdocvw:BindStatusCallback_GetBindInfo (0x114420d8)->(0x34baa8 0x34bab8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12c51548)->((null) 29 2 0x34d560 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x12c51548)
fixme:shdocvw:ClientSite_GetContainer (0x12c51548)->(0x34d570)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x12c51548)->(0xb7e30281)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12c51548)->((null) 25 2 0x34d4a4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12c51548)->((null) 26 2 0x34d4a4 (nil))
fixme:mshtml:HTMLBodyElement_put_scroll (0x1144d618)->(L"no")
fixme:mshtml:HTMLDocument_put_ondragstart (0x12c51f28)
fixme:mshtml:HTMLBodyElement_put_scroll (0x1144d618)->(L"no")
fixme:mshtml:HTMLBodyElement_put_scroll (0x1144d618)->(L"no")
fixme:shdocvw:ClOleCommandTarget_Exec (0x12c51548)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12c51548)->((null) 28 2 0x34d428 (nil))

```

any suggestions?

---

### Post by bobbyg on 2007-12-25
Ok. These wine and wine doors programs are not working for me. They are teasing me. I've installed Steam and WoW (manually of course. cause wine doors had errors downloading the packages) and I still cannot play these games. For WoW I get an error that says the patch  cannot be found after downloading it. And trying CZ it loads the client and after it loads it auto closes and resizes my desktop to minimum resolution. I've tried removing and reinstalling wine, nvidia drivers and the actual games themselves. Is there someone who can help me figure this out. It is acting like Wine is not compatible with my 32bit system.

---

### Post by Josh1 on 2007-12-25
> **bobbyg said:**
> Ok. These wine and wine doors programs are not working for me. They are teasing me. I've installed Steam and WoW (manually of course. cause wine doors had errors downloading the packages) and I still cannot play these games. For WoW I get an error that says the patch  cannot be found after downloading it. And trying CZ it loads the client and after it loads it auto closes and resizes my desktop to minimum resolution. I've tried removing and reinstalling wine, nvidia drivers and the actual games themselves. Is there someone who can help me figure this out. It is acting like Wine is not compatible with my 32bit system.

Firstly, I never use WINE Doors..

I have got WoW and CS (CZ, 1.6, CSS as well as TF2) working.
WoW needed a bit of tinkering, there is a guide to changing the wow settings in the gaming section. CS & Steam I simply do wine steam.exe and it works.

You have installed your video card drivers, right?

---

### Post by bobbyg on 2007-12-25
Yes I have installed the video drivers.I used envy to install the NVIDIA-Linux-x86-169.07-pkg1 driver. My card is a EVGA Nvidia 7950gt ko. I installed Ubuntu a couple days ago, and steam and cz worked with major fps issues. I then tried Fedora 8 64 bit and wine did the same thing with Fedora that it is now doing with Ubuntu. The only common thing is the nvidia driver that I installed. Also when I did load up the login screen for WoW everything was green. Maybe there is something wrong with the OpenGL settings for my linux or wine or possible driver. I read about people installing wine and steam and not having any issues with running cz. So I do not understand why i'm having these issues.

---

### Post by bobbyg on 2007-12-26
Ok thisi s the third post i've made for this. but no-one seems to answer.

Ok. These wine and wine doors programs are not working for me. They are teasing me. I've installed Steam and WoW (manually of course. cause wine doors had errors downloading the packages) and I still cannot play these games. For WoW I get an error that says the patch  cannot be found after downloading it. And trying CZ it loads the client and after it loads it auto closes and resizes my desktop to minimum resolution. I've tried removing and reinstalling wine, nvidia drivers and the actual games themselves. Is there someone who can help me figure this out. It is acting like Wine is not compatible with my 32bit system.

---

### Post by hikaricore on 2007-12-26
Your posts have been merged.  Please refrain from making multiple posts on the same topic.

If someone doesn't answer you it simply means that no one who has read your post has any ideas of how to help.
We're not all just ignoring you, but that could changed with persistant threads on the same topic..

---

