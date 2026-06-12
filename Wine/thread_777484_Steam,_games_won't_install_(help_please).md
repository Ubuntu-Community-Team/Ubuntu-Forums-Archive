---
title: "Steam, games won't install (help please)"
date: 2008-05-01
forum: Wine
---

### Post by smrdelj on 2008-05-01
Hi

After trying a lot, I finally managed to install properly Steam. Now the problem is that, when I select in the tab "My Games" Counter-Strike and click the botton "Install", Steam always cloeses itself.
Suddenly all dissappears and, I guess, Steam shuts down.

Then, if I insist loggin in my Steam account and retrying the action, Steams closes again. It's a circle, always the same.

Anybody knows the solution?

Thanks, excuse my rustic english :$

Bye

---

### Post by aoanla on 2008-05-01
Can you try launching Steam from a terminal 

(by first changing to the Steam install directory with:

cd ~/.wine/drive_c/Program\ Files/Steam/

and then running it in wine with

wine steam.exe

)

and tell us what terminal output you get when Steam crashes, please.

---

### Post by smrdelj on 2008-05-01
Hello. Here's what you asked:

```

CellID: Fetching server list from CSDS. . .
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
CellID: CSDS returned 160 servers.
CellID: Connecting to 116.193.84.100:27031. . .
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
dir: C:\Archivos de programa\Steam\bin\ *.mix
dir: C:\Archivos de programa\Steam\bin\ *.asi
dir: C:\Archivos de programa\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
CellID: Connect to 116.193.84.100:27031 took 561 MS
CellID: Nothing beat our old best time of 153 MS
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
fixme:shdocvw:ViewObject_SetAdvise (0x1fa800)->(1 00000002 0x1194338)
fixme:shdocvw:PersistStreamInit_InitNew (0x1fa800)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1fa800)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1fa800)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x1fae60)->(1 00000002 0x11943a0)
fixme:shdocvw:PersistStreamInit_InitNew (0x1fae60)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1fae60)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1fae60)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x2163f0)->(1 00000002 0x1194a80)
fixme:shdocvw:PersistStreamInit_InitNew (0x2163f0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x2163f0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x2163f0)->(ffffffff)
fixme:iphlpapi:NotifyAddrChange (Handle 0x7b584a08, overlapped 0x7b5849ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x10fbef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x21648c)->((null) 1 0x3285dc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x21648c)->((null) 25 2 0x3285f0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x21648c)->((null) 26 2 0x3285f0 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:shdocvw:ClientSite_GetContainer (0x21648c)->(0x32862c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x21648c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x3286f0 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x217b38)->(L"" L"" 0 0x328728)
fixme:mshtml:fix_headers Ignoring User-Agent header
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,0,2): stub!
fixme:shdocvw:ClOleCommandTarget_Exec (0x21648c)->((null) 29 2 0x32d558 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x21648c)
fixme:shdocvw:ClientSite_GetContainer (0x21648c)->(0x32d508)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x21648c)->(0xf7e717c9)
fixme:shdocvw:ClOleCommandTarget_Exec (0x21648c)->((null) 25 2 0x32d43c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x21648c)->((null) 26 2 0x32d43c (nil))
fixme:mshtml:HTMLBodyElement_put_scroll (0x2180b0)->(L"no")
fixme:mshtml:HTMLDocument_put_ondragstart (0x218b30)
fixme:mshtml:HTMLBodyElement_put_scroll (0x2180b0)->(L"no")
fixme:mshtml:HTMLBodyElement_put_scroll (0x2180b0)->(L"no")
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10038,0x00000000,0,2): stub!
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1fa89c)->((null) 1 0x32a874 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1fa89c)->((null) 25 2 0x32a888 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1fa89c)->((null) 26 2 0x32a888 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:shdocvw:ClientSite_GetContainer (0x1fa89c)->(0x32a8c4)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1fa89c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32a988 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x110ba370)->(L"" L"" 0 0x32a9c0)
fixme:mshtml:fix_headers Ignoring User-Agent header
fixme:shdocvw:ClOleCommandTarget_Exec (0x1fa89c)->((null) 29 2 0x32d558 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1fa89c)
fixme:shdocvw:ClientSite_GetContainer (0x1fa89c)->(0x32d508)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1fa89c)->(0xf7e717c9)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1fa89c)->((null) 25 2 0x32d43c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1fa89c)->((null) 26 2 0x32d43c (nil))
fixme:mshtml:HTMLBodyElement_put_scroll (0x110c8378)->(L"no")
fixme:mshtml:HTMLDocument_put_ondragstart (0x110b62e0)
fixme:mshtml:HTMLBodyElement_put_scroll (0x110c8378)->(L"no")
fixme:mshtml:HTMLBodyElement_put_scroll (0x110c8378)->(L"no")
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,240,2): stub!
fixme:mshtml:HTMLBodyElement_put_scroll (0x110f55c0)->(L"no")
fixme:shdocvw:ClOleCommandTarget_Exec (0x21648c)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x21648c)->((null) 28 2 0x32d420 (nil))
fixme:mshtml:HTMLBodyElement_put_scroll (0x110c8378)->(L"no")
fixme:shdocvw:ClOleCommandTarget_Exec (0x1fa89c)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1fa89c)->((null) 28 2 0x32d420 (nil))
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,232,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,232,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,156,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,156,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,39,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,0,2): stub!
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x2163f0)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x2163f0)
fixme:shdocvw:OleObject_Close (0x2163f0)->(1)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x218b30)->((nil))
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,251,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,248,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,248,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,243,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,240,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,230,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,225,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,222,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,218,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,206,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,197,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,195,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,189,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,178,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,176,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,169,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,167,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,155,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,152,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,149,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,147,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,138,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,136,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,133,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,125,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,122,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,120,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,119,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,112,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,111,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,109,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,108,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,107,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,104,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,96,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,94,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,93,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,92,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,90,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,76,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,57,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,56,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,55,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,53,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,52,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,49,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,48,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,46,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,45,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,38,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,37,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,35,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,34,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,33,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,31,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,30,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,29,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,27,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,26,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,20,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,18,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,16,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,15,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,14,2): stub!
fixme:win:SetLayeredWindowAttributes (0x100b4,0x00000000,12,2): stub!
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
Fallo de segmentación

```

I hope you can help me. Thanks, bye

---

### Post by aoanla on 2008-05-02
Okay, that's odd.

Firstly, can you try installing the winbind package?

---

### Post by smrdelj on 2008-05-02
> **aoanla said:**
> Okay, that's odd.

Firstly, can you try installing the winbind package?Excuse me but, what is winblind?

Should I install it by "sudo apt-get install winblind"?

Thanks. See you

---

### Post by aoanla on 2008-05-02
Firstly, it's called "winbind" not "winblind".
Secondly, it's the network tools package that the first wine error message requests that you install:
> 
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.


And, yes, you can use

sudo apt-get install winbind

to install it, or use Synaptic or any other package management tool.

---

### Post by Rocket2DMn on 2008-05-02
It is giving you a segmentation fault, which means the software is acting incorrectly by attemping to use memory outside its designated range.  You should uninstall steam and reinstall it.  I'm not sure what your original install method was, but you should use steam's installer from their website, then execute it with
```
wine msiexec /i SteamInstall.msi
```

---

### Post by smrdelj on 2008-05-04
Hi, still having problems with this :@

aoanla, I installed winbind and now, when I run Steam by executing "wine Steam.exe" in console, Steam crashes while logging into my account. It suddenly dissappears just before completing the connection to my account, exactly when it's about to finish the logging and launch.
It's exactly like what happened when I couldn't install Gecko.

Here's the terminal output: ```

CellID: Fetching server list from CSDS. . .
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
CellID: CSDS returned 160 servers.
CellID: Connecting to 116.193.88.75:27031. . .
CellID: Connect to 116.193.88.75:27031 took 538 MS
CellID: Nothing beat our old best time of 168 MS
dir: Z:\home\matias\.wine\drive_c\Program Files\Steam\bin\ *.mix
dir: Z:\home\matias\.wine\drive_c\Program Files\Steam\bin\ *.asi
dir: Z:\home\matias\.wine\drive_c\Program Files\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
Corrupt JPEG data: 57 extraneous bytes before marker 0xdb
fixme:shdocvw:ViewObject_SetAdvise (0x1ab040)->(1 00000002 0x1193fb0)
fixme:shdocvw:PersistStreamInit_InitNew (0x1ab040)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1ab040)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1ab040)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x1a8c20)->(1 00000002 0x1194018)
fixme:shdocvw:PersistStreamInit_InitNew (0x1a8c20)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1a8c20)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1a8c20)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x20cd48)->(1 00000002 0x1194718)
fixme:shdocvw:PersistStreamInit_InitNew (0x20cd48)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x20cd48)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x20cd48)->(ffffffff)
Could not load Mozilla. HTML rendering will be disabled.
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x20cde4)->((null) 1 0x3285dc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x20cde4)->((null) 25 2 0x3285f0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x20cde4)->((null) 26 2 0x3285f0 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:shdocvw:ClientSite_GetContainer (0x20cde4)->(0x32862c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x20cde4)->({000214d1-0000-0000-c000-000000000046} 37 0 0x3286f0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x20cde4)->({000214d1-0000-0000-c000-000000000046} 84 0 (nil) 0x328780)
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:urlmon:ObtainUserAgentString (0, 0x326f27, 0x326f20): stub
fixme:urlmon:ObtainUserAgentString (0, 0x211dc8, 0x326f20): stub
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x20f0b0)->(0x326f28 0x326f20 0)
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,0,2): stub!
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set
fixme:dbghelp:dump_system_info fill in CPU vendorID and feature set

```

Rocket2DMn, I always install Steam thatway

Any idea?

Thanks. Bye

[COLOR="Red"]EDIT:[/COLOR] Wine has just updated some component. In consequence, I obtained a new result while running "wine Steam.exe" in terminal. Look at the screen shot: 

[[IMG]http://img232.imageshack.us/img232/9242/pantallazops1.th.png[/IMG]](http://img232.imageshack.us/my.php?image=pantallazops1.png)

---

### Post by smrdelj on 2008-05-04
Here refreshing the thread..

Does anybody know what's happening?

Thanks

---

### Post by Joshgo on 2008-05-04
I've come across same thing, usually I do that thing which restart X server or something (press ctrl+alt+backspace) or restart my computer. That fixed the problem but it comes back on later logins. I don't know whether either of those 2 fixed the problem, but for me it did. How did I fix the problem permanently? Since I recently installed ubuntu, I didn't care much that I was reinstalling it. Reinstalling ubuntu is how I fixed the problem. Other then that, no clue. 

I AM A BEGINNER.

---

### Post by smrdelj on 2008-05-06
When I installed Ubuntu 7.10 and, therefore, installed wine; I could perfectly run Cs 1.6 (No-Steam) and other programs that I tried. 

Now that I upgrade to Hardy, Wine doesn't run ANYTHING. All aplications and programs that I tried, all crashed before start..

I don't know what to do...don't understand

---

### Post by smrdelj on 2008-05-06
I solved the last problem I showed (screenshot, post #8) by deleting the file "ClientRegistry.bob".

Now, while running Steam and attemping to install Cs 1.6; Steam crashes again when I click the "Install" Botton.

Here my terminal output:```

CellID: Fetching server list from CSDS. . .
fixme:process:SetProcessShutdownParameters (00000100, 00000000): partial stub.
CellID: CSDS returned 160 servers.
CellID: Connecting to 208.111.182.250:27031. . .
dir: Z:\home\matias\.wine\drive_c\Program Files\Steam\bin\ *.mix
dir: Z:\home\matias\.wine\drive_c\Program Files\Steam\bin\ *.asi
dir: Z:\home\matias\.wine\drive_c\Program Files\Steam\bin\ *.flt
warning: Unknown nb_ctl request:  4
warning: Unknown nb_ctl request:  30
CellID: Connect to 208.111.182.250:27031 took 266 MS
CellID: Nothing beat our old best time of 176 MS
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:shdocvw:ViewObject_SetAdvise (0x1abab8)->(1 00000002 0x12a3fb8)
fixme:shdocvw:PersistStreamInit_InitNew (0x1abab8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1abab8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1abab8)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x1ac0b0)->(1 00000002 0x12a4020)
fixme:shdocvw:PersistStreamInit_InitNew (0x1ac0b0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1ac0b0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1ac0b0)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x213c20)->(1 00000002 0x12a4890)
fixme:shdocvw:PersistStreamInit_InitNew (0x213c20)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x213c20)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x213c20)->(ffffffff)
fixme:iphlpapi:NotifyAddrChange (Handle 0x7b684a08, overlapped 0x7b6849ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x110def34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x213cbc)->((null) 1 0x3385dc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x213cbc)->((null) 25 2 0x3385f0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x213cbc)->((null) 26 2 0x3385f0 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:shdocvw:ClientSite_GetContainer (0x213cbc)->(0x33862c)
fixme:shdocvw:ClOleCommandTarget_Exec (0x213cbc)->({000214d1-0000-0000-c000-000000000046} 37 0 0x3386f0 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x215408)->(L"" L"" 0 0x338728)
fixme:mshtml:fix_headers Ignoring User-Agent header
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,0,2): stub!
fixme:shdocvw:ClOleCommandTarget_Exec (0x213cbc)->((null) 29 2 0x33d558 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x213cbc)
fixme:shdocvw:ClientSite_GetContainer (0x213cbc)->(0x33d508)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x213cbc)->(0xf7e4a755)
fixme:shdocvw:ClOleCommandTarget_Exec (0x213cbc)->((null) 25 2 0x33d43c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x213cbc)->((null) 26 2 0x33d43c (nil))
fixme:mshtml:HTMLBodyElement_put_scroll (0x111ee0e8)->(L"no")
fixme:mshtml:HTMLDocument_put_ondragstart (0x2167d0)
fixme:mshtml:HTMLBodyElement_put_scroll (0x111ee0e8)->(L"no")
fixme:mshtml:HTMLBodyElement_put_scroll (0x111ee0e8)->(L"no")
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x10038,0x00000000,0,2): stub!
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1abb54)->((null) 1 0x33a874 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1abb54)->((null) 25 2 0x33a888 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1abb54)->((null) 26 2 0x33a888 (nil))
fixme:mshtml:on_change_dlcontrol unsupported dlcontrol 00000070
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:shdocvw:ClientSite_GetContainer (0x1abb54)->(0x33a8c4)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1abb54)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33a988 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x111e8108)->(L"" L"" 0 0x33a9c0)
fixme:mshtml:fix_headers Ignoring User-Agent header
fixme:shdocvw:ClOleCommandTarget_Exec (0x1abb54)->((null) 29 2 0x33d558 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1abb54)
fixme:shdocvw:ClientSite_GetContainer (0x1abb54)->(0x33d508)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1abb54)->(0xf7e4a755)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1abb54)->((null) 25 2 0x33d43c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1abb54)->((null) 26 2 0x33d43c (nil))
fixme:mshtml:HTMLBodyElement_put_scroll (0x1a0a68)->(L"no")
fixme:mshtml:HTMLDocument_put_ondragstart (0x111e3a10)
fixme:mshtml:HTMLBodyElement_put_scroll (0x1a0a68)->(L"no")
fixme:mshtml:HTMLBodyElement_put_scroll (0x1a0a68)->(L"no")
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:mshtml:HTMLBodyElement_put_scroll (0x114bba20)->(L"no")
fixme:shdocvw:ClOleCommandTarget_Exec (0x213cbc)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x213cbc)->((null) 28 2 0x33d420 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1abb54)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1abb54)->((null) 28 2 0x33d420 (nil))
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,225,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,225,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,169,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,169,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,96,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,69,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,25,2): stub!
fixme:win:SetLayeredWindowAttributes (0x1009e,0x00000000,0,2): stub!
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x213c20)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x213c20)
fixme:shdocvw:OleObject_Close (0x213c20)->(1)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x2167d0)->((nil))
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
Fallo de segmentación

```

Nobody? Please Help!

---

