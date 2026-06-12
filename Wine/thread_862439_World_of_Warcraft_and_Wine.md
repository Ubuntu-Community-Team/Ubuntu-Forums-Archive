---
title: "World of Warcraft and Wine"
date: 2008-07-17
forum: Wine
---

### Post by Mister Cuddles on 2008-07-17
Hello, and thank you for helping in advance,

I'm new to ubuntu and the way things work with it, and wine is one of those things I'm not really great with yet. I followed the instructions on [this howto]("https://help.ubuntu.com/community/WorldofWarcraft#head-ffdb6e1abf69e93f2ee1bad73a59c4fc17a295db") with the Alternate Installation Method 2 because I do not have the original disks with me, and I'm noticing I'm have a very very very slow download rate. It's telling me I have near 20hrs for about 3gb worth of game. Considering this is just the WoW Classic and does not include the patches and expansion, I'm a little worried. 

Anyhow, one of the first things I did when I saw I had this unusually slow rate was I ran it in the terminal and this is what I got.

```
alverto@alverto-desktop:~$ wine wowclient-downloader.exe
fixme:shdocvw:PersistStorage_InitNew (0x12f6f0)->(0x4a2cd8)
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d7b6a08, overlapped 0x7d7b69ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x130ef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x12f78c)->((null) 1 0x32c9f8 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12f78c)->((null) 25 2 0x32ca0c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12f78c)->((null) 26 2 0x32ca0c (nil))
fixme:shdocvw:ClientSite_GetContainer (0x12f78c)->(0x32ca48)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12f78c)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32cb0c (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x12fb60)->(L"" L"" 0 0x32cb44)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000

http error code = 404
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:shdocvw:ClOleCommandTarget_Exec (0x12f78c)->((null) 29 2 0x32f45c (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x12f78c)
fixme:shdocvw:ClientSite_GetContainer (0x12f78c)->(0x32f1a8)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x12f78c)->(0xb7dfa6d1)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12f78c)->((null) 25 2 0x32f0dc (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12f78c)->((null) 26 2 0x32f0dc (nil))
fixme:shell:BrsFolder_OnCreate flags BIF_NEWDIALOGSTYLE partially implemented
fixme:bidi:mirror stub: mirroring of characters not yet implemented
fixme:shdocvw:ClOleCommandTarget_Exec (0x12f78c)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12f78c)->((null) 28 2 0x32f194 (nil))
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1
err:ole:CoGetClassObject class {e2085f28-feb7-404a-b8e7-e659bdeaaa02} not registered
err:ole:CoGetClassObject class {e2085f28-feb7-404a-b8e7-e659bdeaaa02} not registered
err:ole:create_server class {e2085f28-feb7-404a-b8e7-e659bdeaaa02} not registered
err:ole:CoGetClassObject no class object {e2085f28-feb7-404a-b8e7-e659bdeaaa02} could be created for context 0x7
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetGetConnectedState always returning LAN connection.

```

and it repeats it for a while and every so often it has 

```
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (60000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 60000
fixme:wininet:InternetGetConnectedState always returning LAN connection.

```

I got the firestarter application and opened the correct ports, and I've opened the ports on my router in the past so I don't need to do that either.

I'm just at a loss, I'd like to not wait a week to get my game fully installed, anyone able to help?

(If I need to add any more information, please tell me so and I'll get right on it)

---

### Post by kdorf on 2008-07-17
The easiest fix is to download in Windows (or in a virtual machine) and then copy the files over to Ubuntu for use.

---

### Post by Mister Cuddles on 2008-07-17
I don't have windows on this computer anymore. It got so bad that I ended up having to reformat, only to realize I didn't have my windows installation disk. So, I went to ubuntu, and I like it more than windows. I just want my games is all =(..

How would I get the files if I don't have windows?

---

### Post by darkaudit on 2008-07-17
A trial version disk is only $1.99 at Best Buy. It's a DVD, not 5 CDs like my original copy is.

WoW uses p2p to distribute patches and the like. Several variables could be at work here for your slow download speeds. Is your router set up properly to allow for transfers? Does your ISP throttle p2p? The former can be addressed with a visit to the WoW tech support site. The latter is gonna be tough.

If you want to go the trial DVD route to install, here's a suggestion: many sites keep older and current patches available for download. They're straight downloads, not p2p like the WoW patcher. Start a download of those before you head out to the store. Some should be done before you get back. (The 2.3 patch is over 700MB)

---

### Post by Mister Cuddles on 2008-07-18
> **darkaudit said:**
> A trial version disk is only $1.99 at Best Buy. It's a DVD, not 5 CDs like my original copy is.

WoW uses p2p to distribute patches and the like. Several variables could be at work here for your slow download speeds. Is your router set up properly to allow for transfers? Does your ISP throttle p2p? The former can be addressed with a visit to the WoW tech support site. The latter is gonna be tough.

If you want to go the trial DVD route to install, here's a suggestion: many sites keep older and current patches available for download. They're straight downloads, not p2p like the WoW patcher. Start a download of those before you head out to the store. Some should be done before you get back. (The 2.3 patch is over 700MB)

I don't have the transportation currently to get to Best Buy right now, and I tried going to fileplanet and such and the transfer rate is just as slow as the blizzard downloader.

---

