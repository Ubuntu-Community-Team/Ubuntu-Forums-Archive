---
title: "Unable to Load Registration Page"
date: 2008-02-05
forum: Wine
---

### Post by ReccaSquirrel on 2008-02-05
Here's the thing.  I was kinda impressed with the Virtual Villagers game and decided to be stupid and pay for the registration.  The game works fine when it runs but I can't get it to allow me to input the registration code.

Basically, the game opens with a splash screen with three options:  Play, Buy, Enter Key.  I'm not entirely sure what each button does because with Wine, it won't bring up or launch anything.  If you launch the program and close this splash screen, the game itself always launched.

And if you are curious, the link for the install file is [here]("http://www.virtualvillagers.com/zips/VVsetup1_01.exe").

Anyway, onto the juicy tidbits.
I'm using Wine 0.9.54 (just updated)
I've installed the game in question and through Wine-Doors, I've installed Firefox 2.0.
I'm using no overrides and haven't messed with any of the Wine configuration settings at all.
I've tried XP, NT 4.0, and 2000 to run the program, same issue everytime.

```
joshua@Aldaric:~/.wine/drive_c/Program Files/Virtual Villagers$ wine VirtualVillagers.exe
fixme:reg:RegSetKeySecurity :(0x80,4,0x397e00): stub
err:mshtml:check_version Could not open VERSION file
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x21736c)->((null) 1 0x3480d0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x21736c)->((null) 25 2 0x3480e4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x21736c)->((null) 26 2 0x3480e4 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x21736c)->(0x348120)
fixme:shdocvw:ClOleCommandTarget_Exec (0x21736c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x3481dc (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x219948)->(L"" L"" 0 0x348210)
fixme:shdocvw:BindStatusCallback_GetBindInfo (0x219948)->(0x348214 0x348224)
fixme:shdocvw:ClOleCommandTarget_Exec (0x21736c)->((null) 29 2 0x347e98 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x21736c)
fixme:shdocvw:ClientSite_GetContainer (0x21736c)->(0x347d84)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x21736c)->(0xb7e02109)
fixme:shdocvw:ClOleCommandTarget_Exec (0x21736c)->((null) 25 2 0x347cb8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x21736c)->((null) 26 2 0x347cb8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x21736c)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x21736c)->((null) 28 2 0x347d10 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x21736c)->((null) 26 2 0x347e78 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x21736c)->((null) 29 2 0x347e88 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x21736c)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x21736c)->((null) 35 0 (nil) (nil))
fixme:shdocvw:InPlaceFrame_SetStatusText (0x21736c)->(0x7bc9e7c0)
fixme:shdocvw:WebBrowser_Quit (0x2172d8)
joshua@Aldaric:~/.wine/drive_c/Program Files/Virtual Villagers$ 
```
Any help is appreciated even if it is where to go in regedit to manually enter the key.

On a somewhat off-topic note, I'd love to learn more about Ubuntu so if you have any recommendations for books on the subject, please share.

I checked AppDB but couldn't find the game on there and the site seems down at this time anyway.

---

### Post by ReccaSquirrel on 2008-02-05
I forgot to mention that I'm on 7.10 (Gutsy?)

---

### Post by ReccaSquirrel on 2008-02-06
Anyone have any ideas.  I tried a couple of things using the Things I Learned About Wine thread but had no luck.

---

### Post by ReccaSquirrel on 2008-02-06
Still no luck with anything I've tried so far.

---

### Post by ReccaSquirrel on 2008-02-06
If it helps, by manner of research, the problem is that the registration dialog box is what is not appear.

---

