---
title: "Please help with steam and wine,"
date: 2008-02-27
forum: Wine
---

### Post by dew5 on 2008-02-27
Hey people.

When I enter

 env WINEPREFIX="/home/david/.wine" wine "C:\Program Files\Steam\Steam.exe

to launch steam, I get this output

Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
dir: C:\Program Files\Steam\bin\ *.mix
dir: C:\Program Files\Steam\bin\ *.asi
dir: C:\Program Files\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
fixme:shdocvw:ViewObject_SetAdvise (0x1ac1c0)->(1 00000002 0x14de148)
fixme:shdocvw:PersistStreamInit_InitNew (0x1ac1c0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1ac1c0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1ac1c0)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x1ac808)->(1 00000002 0x14de1b0)
fixme:shdocvw:PersistStreamInit_InitNew (0x1ac808)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1ac808)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1ac808)->(ffffffff)
fixme:win:SetLayeredWindowAttributes (0x2002a,0x00000000,0,2): stub!
Could not load Mozilla. HTML rendering will be disabled.
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1ac258)->((null) 1 0x33b770 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ac258)->((null) 25 2 0x33b798 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ac258)->((null) 26 2 0x33b798 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:shdocvw:ClientSite_GetContainer (0x1ac258)->(0x33b7e4)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ac258)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33b8f8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ac258)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x33b968)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x339cdb, 0x339cdc): stub
fixme:urlmon:ObtainUserAgentString (0, 0x1caca8, 0x339cdc): stub
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x1ca328)->(0x33a0f8 0x339cdc 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ac258)->((null) 29 2 0x33c0b8 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1ac258)
fixme:shdocvw:ClientSite_GetContainer (0x1ac258)->(0x33c068)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1ac258)->(0xb7ed5734)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ac258)->((null) 25 2 0x33bf7c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1ac258)->((null) 26 2 0x33bf7c (nil))
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
 and steam doesn't start. Can someone please help.

---

### Post by Tadock on 2008-02-27
It could not initiate the OpenGL is your graphics driver installed? Also, could you list some hardware specs?

---

### Post by jeffus_il on 2008-02-27
Sounds like an invitation for a drink in the sauna.

---

### Post by dew5 on 2008-03-09
Thanks for the quick response.

You were right Tadock, Thank you . I have since enabled my nvidia grafix drivers for my NVIDIA GeForce 7500LE card.

Hardware spect are pentium D processor 820 (core duo), 1024MB ram, 7200RPM Serial ATA hard drive, NVIDIA GeForce 7500LE.

However I am still unable to launch steam. It begins to launch , but as soon as it opens steam menu it crashes.

Also i am unable to enter
env WINEPREFIX="/home/david/.wine" wine "C:\Program Files\Steam\Steam.exe

to start the steam app in the terminal it just goes to 
>

and does not start steam.
I can launch steam though the wine app in "application", how ever as I said, It gets to the steam menu  then crashes.

Please help.

oh BTW Jeffus_il, That comment went way over my head(i.e i didn't get it). You'll have to explain in laymen terms.
So please help.

dew5

---

### Post by dew5 on 2008-03-09
Ok so the new command is

env WINEPREFIX="/home/david/.wine" wine "C:\Program Files\Steam\Steam.exe"

and the output is:

ALSA lib pcm_mmap.c:369:(snd_pcm_mmap) mmap failed: Invalid argument
fixme:mixer:ALSA_MixerInit No master control found on SAA7134, disabling mixer
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
dir: C:\Program Files\Steam\bin\ *.mix
dir: C:\Program Files\Steam\bin\ *.asi
dir: C:\Program Files\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
fixme:shdocvw:ViewObject_SetAdvise (0xff202d8)->(1 00000002 0x146e390)
fixme:shdocvw:PersistStreamInit_InitNew (0xff202d8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xff202d8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xff202d8)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x10895458)->(1 00000002 0x146e3f8)
fixme:shdocvw:PersistStreamInit_InitNew (0x10895458)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x10895458)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x10895458)->(ffffffff)
fixme:win:SetLayeredWindowAttributes (0x10098,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002a,0x00000000,0,2): stub!
Could not load Mozilla. HTML rendering will be disabled.
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0xff20374)->((null) 1 0x33a720 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xff20374)->((null) 25 2 0x33a748 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xff20374)->((null) 26 2 0x33a748 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:shdocvw:ClientSite_GetContainer (0xff20374)->(0x33a794)
fixme:shdocvw:ClOleCommandTarget_Exec (0xff20374)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33a8a8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xff20374)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x33a918)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x338c8b, 0x338c8c): stub
fixme:urlmon:ObtainUserAgentString (0, 0x10822fd0, 0x338c8c): stub
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x1085b480)->(0x3390a8 0x338c8c 0)
fixme:shdocvw:ClOleCommandTarget_Exec (0xff20374)->((null) 29 2 0x33c0b8 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0xff20374)
fixme:shdocvw:ClientSite_GetContainer (0xff20374)->(0x33c068)
fixme:shdocvw:InPlaceFrame_SetStatusText (0xff20374)->(0xb7e9eb74)
fixme:shdocvw:ClOleCommandTarget_Exec (0xff20374)->((null) 25 2 0x33bf7c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xff20374)->((null) 26 2 0x33bf7c (nil))
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set

Any help available?

---

### Post by doorknob60 on 2008-03-10
Go to a terminal and type this:
```
wine iexplore http://google.com
```
Then it will ask you if you want to install the Gecko engine, say yes. Then try steam again.

---

### Post by BloodyFreeze on 2008-03-12
I've had the exact same problem. Many people have had this problem with the new wine as well. Gecko Did not solve this problem. It was automatically installed during the first boot of steam, which crashed any ways when i got to the actual steam page. Disabling the update page does not keep it from crashing either. all necessary fonts are installed. Gecko and all necessary files for gecko are installed. Problem persists. I am using Kubuntu 7.10. I am really running out of ideas. going back to an older version of wine may be the answer to this problem for now

---

