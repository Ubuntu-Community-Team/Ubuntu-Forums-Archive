---
title: "Voyage Century..."
date: 2007-03-11
forum: Wine
---

### Post by Mr. Picklesworth on 2007-03-11
Hi folks.
I discovered a game called Voyage Century a while ago. I'm not a fan of their little spamming rampage, but I have been meaning to look at it anyway.
Has anyone got it running in Ubuntu via Wine?

1.0 is listed at WineHQ's AppDB (and it's fairly recently posted), but it says the mouse doesn't work. Perhaps Feisty or the latest version of the game has this fixed?
[http://appdb.winehq.org/appview.php?iVersionId=7054](http://appdb.winehq.org/appview.php?iVersionId=7054)

---

### Post by mandlebaum on 2007-06-08
I have gotten it working in wine .36 and .37.  However, there is no sound and during scene changes  between rooms there is a chance that the entire program crashes.  The program likes to eat memory, so after it crashes if you want to relogin its usually best to kill the wineserver and then start again.

---

### Post by TKR101010 on 2007-11-11
I got it to work easily in Feisty, but have not been able to get past logon since installing Gutsy. :(

---

### Post by TKR101010 on 2007-11-14
OK, well at least part of the problem I was having in Gusty was my video driver, which I got figured out. Now I can get the program to start up, log in to the server, and then get to the character selection screen. Once you select a character  the programs loads the world, but then suddenly quits. Here's the messages from the terminal from start to finish of the process just described ...

```

user@D4T2:~$ cd '/home/user/.wine/drive_c/Program Files/Voyage Century Online'
user@D4T2:~/.wine/drive_c/Program Files/Voyage Century Online$ wine voyagecentury.exe
fixme:shdocvw:WebBrowser_QueryInterface (0x12cf10)->({bd1ae5e0-a6ae-11ce-bd37-504200c10000} 0x34e0d0) interface not supported
fixme:shdocvw:PersistStreamInit_Load (0x12cf10)->(0x34e09c)
fixme:shdocvw:OleControl_FreezeEvents (0x12cf10)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x12cf10)->(0)
fixme:iphlpapi:NotifyAddrChange (Handle 0x72eee9f8, overlapped 0x72eee9dc): stub
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x12cfa4)->((null) 1 0x34c914 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12cfa4)->((null) 25 2 0x34c928 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12cfa4)->((null) 26 2 0x34c928 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x12cfa4)->(0x34c964)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12cfa4)->({000214d1-0000-0000-c000-000000000046} 37 0 0x34ca20 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x144768)->(L"" L"" 0 0x34ca54)
fixme:shdocvw:BindStatusCallback_GetBindInfo (0x144768)->(0x34ca58 0x34ca68)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12cfa4)->((null) 29 2 0x34e5c4 (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x12cfa4)
fixme:shdocvw:ClientSite_GetContainer (0x12cfa4)->(0x34e5e4)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x12cfa4)->(0xb7eae109)
fixme:shdocvw:ClOleCommandTarget_Exec (0x12cfa4)->((null) 25 2 0x34e518 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12cfa4)->((null) 26 2 0x34e518 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12cfa4)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12cfa4)->((null) 28 2 0x34e570 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12cfa4)->((null) 26 2 0x34e5a4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12cfa4)->((null) 29 2 0x34e5b4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12cfa4)->({de4ba900-59ca-11cf-9592-444553540000} 2315 0 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x12cfa4)->((null) 35 0 (nil) (nil))
fixme:shdocvw:InPlaceFrame_SetStatusText (0x12cfa4)->(0x7bc9e56f)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x12cf10)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x144a90)->((nil))
fixme:shdocvw:OleObject_Close (0x12cf10)->(1)
fixme:shell:DllCanUnloadNow stub
user@D4T2:~/.wine/drive_c/Program Files/Voyage Century Online$ fixme:win:EnumDisplayDevicesW ((null),0,0x346bc8,0x00000000), stub!
fixme:d3d8:ValidateVertexShader (0x335bbe0 (nil) (nil) 1 0x346464): stub
fixme:d3d8:ValidatePixelShader (0x335cdd8 (nil) 1 0x346464): stub
fixme:d3d8:ValidatePixelShader (0x335a1b8 (nil) 1 0x346464): stub
fixme:d3d8:ValidateVertexShader (0x335a268 (nil) (nil) 1 0x346464): stub
fixme:d3d8:ValidatePixelShader (0x335cd80 (nil) 1 0x346464): stub
fixme:d3d8:ValidatePixelShader (0x335caf8 (nil) 1 0x346464): stub
fixme:d3d8:ValidatePixelShader (0x335bc90 (nil) 1 0x346464): stub
fixme:d3d8:ValidateVertexShader (0x3356dd0 (nil) (nil) 1 0x346464): stub
fixme:d3d8:ValidatePixelShader (0x335cc90 (nil) 1 0x346464): stub
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:d3d8:IDirect3DDevice8Impl_CreateVertexBuffer (0x12a068) call to IWineD3DDevice_CreateVertexBuffer failed
fixme:winmm:MMDRV_Exit Closing while ll-driver open

```

The last three lines of that are when you click to enter the world from character selection. Anyone have any ideas on what I should do next?

---

### Post by TKR101010 on 2007-11-16
Just thought I'd give this thread a bump ...

---

### Post by Squirrelboy38 on 2008-02-11
Hi I have played VCO as well. And since I've gone from Windows to Ubuntu I haven't played and have been trying to get back in. I am currently using Gutsy and also having the same issues. Wine gets it up and going log in, select character, goes to the loading screen and then crashes. I have no clue on any of this as I am a noob. Any help any one can give about this issue and Wine would be WONDERFUL as I want to play too.

---

### Post by kardamas2 on 2008-07-11
i tried to play voyage on wine 1.0,
it starts normally, but i have problem in log in page...
the ship and dolphins are black and the other white...
i don't know why this take place...
my voice is normally correct...
if anyone had the same problem and solve it plz let me know...

P.S. if you want guild Crusaders will accept you

---

### Post by AngelBreath on 2008-10-05
Trying to install the game in Hardy. Installation was very easy...the game starts, but after the login screen and the character select, it closes. No idea how to make it work.

P.S (Using Wine of course).

---

### Post by Malik on 2009-08-21
man i want to play this :(

---

