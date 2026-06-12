---
title: "Age Of Wushu"
date: 2012-11-29
forum: Wine
---

### Post by offnix on 2012-11-29
Hi all,

I have tried this new MMORPG Age Of Wushu, currently between closed beta 1 and closed beta 2.
it works fin on windows, and work on ubuntu 12.10 using wine(except theres no text).

i have tried addin fonts like fake chinese and japanse and such, added directx9 and the 43dll, tried with no-dwrite, tested as WinXP, Vista, Win7 and even Win 8, text just won't show in launcher and game.

i'm out of ideeas on what to try next, and would really appreciate a hand on this matter as the game is very nice.

here are some pictures on how it looks without text:
[http://www39.zippyshare.com/scaled/98740670/file.html](http://www39.zippyshare.com/scaled/98740670/file.html)
[http://www39.zippyshare.com/scaled/54734803/file.html](http://www39.zippyshare.com/scaled/54734803/file.html)

this is how it should look with text:
[http://www1.zippyshare.com/scaled/42986622/file.html](http://www1.zippyshare.com/scaled/42986622/file.html)

Heres the appdb link: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=27165](http://appdb.winehq.org/objectManager.php?sClass=version&iId=27165)

Thanks,
Off Nix

---

### Post by offnix on 2012-12-18
Hi all,

Glad to let you know now it should work.
Notes:
version of game: 0.0.1.012
version of WINE: 1.5.19
version of Ubuntu: 12.10.x64

Guide is as follows:

The following needs to be done to work properly:
**_Method 1_**
1) Copy from game client: \path_to_game\Age of Wushu\bin
the following 2 files: d3dx9_35.dll & gdiplus.dll
2) Paste it in your home directory under:
\home\[username]\.wine\drive_c\windows\system32
3) With winecfg, make sure you set Default OS to Windows 7
4) With winetricks, install the followings: d3dx9_35 & gdiplus
5) In winecfg at Library tab, add dwrite, edit and set to disable
6) start game from a new shortcut or from terminal with the following command: wine fxlaunch.exe -no-dwrite

**_Method 2_**
Is same as Method 1, but skip the following steps: 1), 2) & 5)

**_Method 3_**
Previous to step 1), you need to:
0.a) use winetricks to install all fake fonts, chinese, japanese, and such
0.b) need to install both in linux fonts and wine fonts(\home\[username]\.wine\drive_c\windows\Fonts\) the game fonts. uploaded here: font_pack.7z
[http://www68.zippyshare.com/v/21873071/file.html](http://www68.zippyshare.com/v/21873071/file.html)
MD5sum: b6171275e176eb9cd3bb27d659bab6d9 *font_pack.7z

Game Screenshots:
AoW1.png
[http://www56.zippyshare.com/v/26991674/file.html](http://www56.zippyshare.com/v/26991674/file.html)

AoW2.png
[http://www59.zippyshare.com/v/18509072/file.html](http://www59.zippyshare.com/v/18509072/file.html)

AoW3.png
[http://www10.zippyshare.com/v/51861398/file.html](http://www10.zippyshare.com/v/51861398/file.html)

AoW4.png
[http://www12.zippyshare.com/v/74740478/file.html](http://www12.zippyshare.com/v/74740478/file.html)

AoW5.png
[http://www22.zippyshare.com/v/19603682/file.html](http://www22.zippyshare.com/v/19603682/file.html)

---

### Post by kajali on 2013-01-09
Yeah this game is good ! So different from others MMO. And I have posted my reviews on the sites [http://www.dotmmo.com/age-of-wushu-6416.html](http://www.dotmmo.com/age-of-wushu-6416.html) and [http://www.mmowood.com/age-of-wushu](http://www.mmowood.com/age-of-wushu) . I am glad to share them with other players.

---

### Post by jhcloud8 on 2013-01-12
I'm getting an error after loading into the game.  Fonts all work following method 1 but right when entering the game it give me an error sddyn01.dll (can't read the rest).  Everything seems to load, but hangs after that.

---

### Post by jigo3392 on 2013-04-11
Hi

Help me please. When I click on the play button closes the game.  

this is what the terminal shows

```
~/.wine/drive_c/Program Files (x86)/Snail Games USA/Age of Wushu$ fixme:heap:HeapSetInformation 0x6b4000 0 0x33f260 4
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180, std (d/m/y): 0/00/0000, dlt (d/m/y): 0/00/0000
fixme:win:EnumDisplayDevicesW ((null),0,0x33e178,0x00000000), stub!
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:win:EnumDisplayDevicesW ((null),0,0x33e198,0x00000000), stub!
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:d3d9 irect3DShaderValidatorCreate9 stub
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:wininet:CommitUrlCacheEntryInternal file of size b4 bytes fills cache
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:ieframe ersistStorage_InitNew (0x37e5df8)->(0x1038fc30)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:ieframe ersistStorage_InitNew (0x37db6e0)->(0x1038fc30)
fixme:urlmon:URLMoniker_BindToObject use running object table
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Thu, 11-Apr-2013 04:35:23 GMT; path=/; domain=.ageofwushu.com; HttpOnly")
fixme:wininet:set_cookie httponly not handled (L"HttpOnly")
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Thu, 01-Jan-1970 00:00:01 GMT; path=/")
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Thu, 11-Apr-2013 04:35:23 GMT; path=/; domain=.ageofwushu.com; HttpOnly")
fixme:wininet:set_cookie httponly not handled (L"HttpOnly")
fixme:wininet:set_cookie persistent cookies not handled (L"expires=Thu, 01-Jan-1970 00:00:01 GMT; path=/")
p11-kit: couldn't load module: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: /usr/lib/i386-linux-gnu/pkcs11/gnome-keyring-pkcs11.so: no se puede abrir el archivo del objeto compartido: No existe el archivo o el directorio
fixme:dwmapi: DwmIsCompositionEnabled 0x6abae480
fixme:iphlpapi:NotifyAddrChange (Handle 0x496e8cc, overlapped 0x496e8b0): stub
fixme:ieframe:ClOleCommandTarget_QueryStatus (0x37e5eac)->((null) 1 0x33e5a4 (nil))
fixme:ieframe:ClOleCommandTarget_QueryStatus command_0: 27, 0x0
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:mshtml:OleControl_OnAmbientPropertyChange V_VT(res)=0
fixme:mshtml: On_change_dlcontrol unsupported dlcontrol 0033e510
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_PALETTE
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 37 of group {000214d1-0000-0000-c000-000000000046}
fixme:ntdll:NtLockFile I/O completion on lock not implemented yet
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x2f6d5c0)->()
fixme:ieframe:ClientSite_GetContainer (0x37e5eac)->(0x33e5b4)
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 84 of group {000214d1-0000-0000-c000-000000000046}
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x2f6d5c0)->(0x33d88c)
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:ieframe:ClOleCommandTarget_QueryStatus (0x37db794)->((null) 1 0x33e5a4 (nil))
fixme:ieframe:ClOleCommandTarget_QueryStatus command_0: 27, 0x0
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:mshtml:OleControl_OnAmbientPropertyChange V_VT(res)=0
fixme:mshtml: On_change_dlcontrol unsupported dlcontrol 0033e510
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_USERAGENT
fixme:mshtml:OleControl_OnAmbientPropertyChange not supported AMBIENT_PALETTE
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 37 of group {000214d1-0000-0000-c000-000000000046}
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x37da6d0)->()
fixme:ieframe:ClientSite_GetContainer (0x37db794)->(0x33e5b4)
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 84 of group {000214d1-0000-0000-c000-000000000046}
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x37da6d0)->(0x33d88c)
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:ieframe: PocHostUIHandler_GetDropTarget (0x37e5eac)
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:ieframe: DocHostUIHandler_GetDropTarget (0x37db794)
fixme:ieframe:ClientSite_GetContainer (0x37e5eac)->(0x33ef04)
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x583c4c0)->()
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x58ba370)->()
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x58e7348)->()
fixme:win:EnumDisplayDevicesW ((null),0,0x33ca08,0x00000000), stub!
fixme:imm:ImmReleaseContext (0x20248, 0x33c2048): stub
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x5863c28)->(0x33ea54 0x33ea2c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x5864168)->(0x33ea54 0x33ea2c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x583c1c8)->(0x33ea54 0x33ea2c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x58b9df0)->(0x33ea54 0x33ea2c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x58baa58)->(0x33ea54 0x33ea2c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x58e6d90)->(0x33ea54 0x33ea2c 0)
fixme:ieframe:ClientSite_GetContainer (0x37db794)->(0x33ef04)
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 25
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x2b45920)->()
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x2b455c0)->()
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x2b44cc0)->()
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x37d97a0)->()
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x2b44568)->(0x33ea54 0x33ea2c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x2b45448)->(0x33ea54 0x33ea2c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x2b44a80)->(0x33ea54 0x33ea2c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x37d9560)->(0x33ea54 0x33ea2c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x2b49418)->(0x33ea54 0x33ea2c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x2b49d68)->(0x33ea54 0x33ea2c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x2b4a1d0)->(0x33ea54 0x33ea2c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x2b4a480)->(0x33ea54 0x33ea2c 0)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x583c4c0)->(0x33df98)
fixme:wininet:CommitUrlCacheEntryInternal file of size 997 bytes fills cache
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x58ba370)->(0x33df98)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x58e7348)->(0x33df98)
fixme:wininet:CommitUrlCacheEntryInternal file of size 3691 bytes fills cache
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x2b45920)->(0x33df98)
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 28
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 28
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x2b455c0)->(0x33df98)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x2b44cc0)->(0x33db98)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x37d97a0)->(0x33df98)
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal file of size 984e bytes fills cache
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetContentLength (0x3654628)->(0x33e160)
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetContentLength (0x5863e20)->(0x33e160)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetContentLength (0x2b45a08)->(0x33e160)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetContentLength (0x2b44618)->(0x33dd60)
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetContentLength (0x2b4a0c0)->(0x33e160)
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetContentLength (0x2b4a378)->(0x33e160)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetContentLength (0x583c078)->(0x33dd60)
fixme:wininet:CommitUrlCacheEntryInternal file of size 27e8 bytes fills cache
fixme:wininet:CommitUrlCacheEntryInternal file of size 27e8 bytes fills cache
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 84 of group {000214d1-0000-0000-c000-000000000046}
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 69 of CGID_Explorer
fixme:ieframe:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 69 of CGID_Explorer
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 103 of group {000214d1-0000-0000-c000-000000000046}
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 2315 of group {de4ba900-59ca-11cf-9592-444553540000}
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 35
fixme:mshtml:nsChannel_IsNoCacheResponse (0x2f6d5c0)->(0x33dc5c)
fixme:wininet:CommitUrlCacheEntryInternal file of size 9a2d bytes fills cache
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 69 of CGID_Explorer
fixme:ieframe:PropertyNotifySink_OnChanged unimplemented dispid 1005
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 69 of CGID_Explorer
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x5859858)->(0x33e654 0x33e62c 0)
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 84 of group {000214d1-0000-0000-c000-000000000046}
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x5bf5ac0)->()
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x5bfb110)->()
fixme:mshtml:nsHttpChannelInternal_SetDocumentURI (0x5baac60)->()
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x5bf7fe8)->(0x33ea54 0x33ea2c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x5baa3f8)->(0x33ea54 0x33ea2c 0)
fixme:mshtml:HttpNegotiate_GetRootSecurityId (0x5bfdef0)->(0x33ea54 0x33ea2c 0)
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_GetContentLength (0x365aa30)->(0x33e160)
fixme:wininet:CommitUrlCacheEntryInternal file of size 9a2d bytes fills cache
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x5bf5ac0)->(0x33db98)
fixme:wininet:CommitUrlCacheEntryInternal file of size 57a3 bytes fills cache
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x5bfb110)->(0x33df98)
fixme:wininet:CommitUrlCacheEntryInternal entry already in cache - don't know what to do!
fixme:wininet:InternetLockRequestFile STUB
fixme:mshtml:nsChannel_IsNoCacheResponse (0x5baac60)->(0x33df98)
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 26
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 29
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 103 of group {000214d1-0000-0000-c000-000000000046}
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 2315 of group {de4ba900-59ca-11cf-9592-444553540000}
fixme:ieframe:ClOleCommandTarget_Exec Unimplemented cmdid 35
fixme:mshtml:nsChannel_IsNoCacheResponse (0x37da6d0)->(0x33decc)
fixme:wininet:CommitUrlCacheEntryInternal file of size b01 bytes fills cache
fixme:ping:main this command currently just sleeps based on -n parameter
fixme:ping:main this command currently just sleeps based on -n parameter
fixme:ping:main this command currently just sleeps based on -n parameter
fixme:heap:HeapSetInformation 0x7d5000 0 0x33f17c 4
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 180, std (d/m/y): 0/00/0000, dlt (d/m/y): 0/00/0000
fixme:win:EnumDisplayDevicesW ((null),0,0x33e18c,0x00000000), stub!
fixme:d3d:debug_d3dformat Unrecognized 0x5a574152 (as fourcc: RAWZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a574152) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x5a534552 (as fourcc: RESZ) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x5a534552) in the format lookup table
fixme:d3d:debug_d3dformat Unrecognized 0x434f5441 (as fourcc: ATOC) WINED3DFORMAT!
fixme:d3d:wined3d_get_format Can't find format unrecognized (0x434f5441) in the format lookup table
fixme:win:EnumDisplayDevicesW ((null),0,0x33e514,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33dd90,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33dd90,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33e148,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x33e148,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33e514,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33e078,0x00000000), stub!
```

---

### Post by winenoob on 2013-05-07
Hello, i'm getting stuck at this part to run the game. i use wine, x11 and xcode to installed wushu, and i'm a noob to linux to run window. because my cd drive is mess up so i can't run bootcamp nor parallel. i run the game the text is pretty chop up and the first time i click play and it just stuck there. and after i did some copy and pasted the two dll to system 32(took me a day to figure it out how to do copy and paste on command line, pardon my noob skill) when i click play a warning message show, probably saying graph is need to be config. and i found the one and only post which is yours to get around this problem, but i don't know how to install winetrick, i do not have wget only curl. could you walk me through this? i'm following method 1. i think i already get the first two steps nail down, but if you could baby step walk me through it again it will be awesome. please don't mind the noob skill i have on this awesome yet difficult language. please help me out please please please. i will salute to you in age of wushu when i get it running. thank you for your time

---

