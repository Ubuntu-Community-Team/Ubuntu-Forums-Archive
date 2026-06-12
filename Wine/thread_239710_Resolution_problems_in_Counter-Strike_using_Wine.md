---
title: "Resolution problems in Counter-Strike using Wine"
date: 2006-08-19
forum: Wine
---

### Post by pihl on 2006-08-19
Hi there!

I'm using Kubuntu Dapper Drake on my HP laptop with ATI radeon x600 mobility graphics card, 1024 mb ram, 1440 x 990 screen resolution (widescreen).
I'm using the latest version of wine (0.9.19) and also the latest linux kernel (source of my problems?)
OpenGL should be up and working correctly.

I've followed several guides on how to install Counter-Strike, including my dear friend Magnus's guide, [http://cslinux.hacka.net](http://cslinux.hacka.net).

I've come so far that I've installed Steam and Counter-Strike, and when I start CS, I get into the menu, but I cant select anything due to the resolution (it's cropped to the top left corner at a very low resolution).

I'm starting the game with the launch options:
-width 1024 -height 768 -heapsize 512000
However, should I change these to widescreen aspect ratio to match my resolution?
[http://www.satf.net/upload/cserror1.png](http://www.satf.net/upload/cserror1.png)

That's how it looks when I start it with the launch options mentioned above. (This was actually not the 'error' I used to get, when the parameter -fullscreen is used, I get that little screen cropped to the whole screen, quite terrible you could say).

Oh, and 75% of the time when I launch either Steam or Counter-Strike I get an error:
```
ERROR
Steam.exe (main exception): Win32 StructuredException at 72E19447 :
Attempt to read from virtual address 0 without appropriate access rights.
```
and Konsole gives me:
```
pihl@pihl-laptop:~/.wine/drive_c/Program Files/Steam$ wine Steam.exe -fullscreen -applaunch 10 -width 1024 -height 768 -heapsize 512000
fixme:shdocvw:ViewObject_SetAdvise (0xd678198)->(1 00000002 0x1121810)
fixme:shdocvw:PersistStreamInit_InitNew (0xd678198)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xd678198)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xd678198)->(ffffffff)
fixme:shdocvw:WebBrowser_put_Silent (0xd678198)->(ffffffff)
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0xd678234)->((null) 1 0x33d410 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd678234)->((null) 25 0 0x33d424 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd678234)->((null) 26 0 0x33d424 (nil))
fixme:shdocvw:ClDispatch_Invoke (0xd678234)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d378 0x33d3c4 (nil) 0x33d388)
fixme:shdocvw:ClDispatch_Invoke (0xd678234)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d338 0x33d384 (nil) 0x33d348)
fixme:shdocvw:ClDispatch_Invoke (0xd678234)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d378 0x33d3c4 (nil) 0x33d388)
fixme:shdocvw:ClDispatch_Invoke (0xd678234)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d338 0x33d384 (nil) 0x33d348)
fixme:shdocvw:ClDispatch_Invoke (0xd678234)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d378 0x33d3c4 (nil) 0x33d388)
fixme:shdocvw:ClDispatch_Invoke (0xd678234)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d378 0x33d3c4 (nil) 0x33d388)
fixme:shdocvw:ClDispatch_Invoke (0xd678234)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d378 0x33d3c4 (nil) 0x33d388)
fixme:shdocvw:ClientSite_GetContainer (0xd678234)->(0x33d450)
fixme:shdocvw:ClOleCommandTarget_Exec (0xd678234)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33d554 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0xd6ed130)->(L"" L"" 0 0x33d568)
fixme:shdocvw:BindStatusCallback_GetBindInfo (0xd6ed130)->(0x33d56c 0x33d4b0)
fixme:shdocvw:ClientSite_GetContainer (0xd678234)->(0x33d75c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0xd678234)->(0xb7ecc3d3)
fixme:shdocvw:ClOleCommandTarget_Exec (0xd678234)->((null) 25 0 0x33d698 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd678234)->((null) 26 0 0x33d698 (nil))
fixme:mshtml:HTMLTextContainer_get_scrollWidth (0xeb723ac)->(0xb5246e0)
fixme:mshtml:HTMLTextContainer_get_scrollHeight (0xeb723ac)->(0xb5246e4)
fixme:mshtml:HTMLTextContainer_get_scrollWidth (0xeb723ac)->(0xb5246e0)
fixme:mshtml:HTMLTextContainer_get_scrollHeight (0xeb723ac)->(0xb5246e4)
fixme:mshtml:HTMLTextContainer_get_scrollWidth (0xeb723ac)->(0xb5246e0)
fixme:mshtml:HTMLTextContainer_get_scrollHeight (0xeb723ac)->(0xb5246e4)
err:systray:delete_icon invalid tray icon ID specified: 1d
fixme:process:SetProcessWorkingSetSize (0xffffffff,-1,-1): stub - harmless
fixme:mshtml:HlinkTarget_SetBrowseContext (0xd6ed2a8)->((nil))
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0xd678234)->((null) 1 0x33d318 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd678234)->((null) 25 0 0x33d32c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd678234)->((null) 26 0 0x33d32c (nil))
fixme:shdocvw:ClDispatch_Invoke (0xd678234)->(-709 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d280 0x33d2cc (nil) 0x33d290)
fixme:shdocvw:ClDispatch_Invoke (0xd678234)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d240 0x33d28c (nil) 0x33d250)
fixme:shdocvw:ClDispatch_Invoke (0xd678234)->(-5501 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d280 0x33d2cc (nil) 0x33d290)
fixme:shdocvw:ClDispatch_Invoke (0xd678234)->(-5512 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d240 0x33d28c (nil) 0x33d250)
fixme:shdocvw:ClDispatch_Invoke (0xd678234)->(-5502 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d280 0x33d2cc (nil) 0x33d290)
fixme:shdocvw:ClDispatch_Invoke (0xd678234)->(-5513 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d280 0x33d2cc (nil) 0x33d290)
fixme:shdocvw:ClDispatch_Invoke (0xd678234)->(-726 {00000000-0000-0000-0000-000000000000} 2048 0002 0x33d280 0x33d2cc (nil) 0x33d290)
fixme:shdocvw:ClientSite_GetContainer (0xd678234)->(0x33d358)
fixme:shdocvw:ClOleCommandTarget_Exec (0xd678234)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33d45c (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0xf792380)->(L"" L"" 0 0x33d470)
fixme:shdocvw:BindStatusCallback_GetBindInfo (0xf792380)->(0x33d474 0x33d3b8)
fixme:shdocvw:ViewObject_SetAdvise (0xd704e48)->(1 00000002 0x1122038)
fixme:shdocvw:PersistStreamInit_InitNew (0xd704e48)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xd704e48)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xd704e48)->(ffffffff)
fixme:shdocvw:WebBrowser_put_Silent (0xd704e48)->(ffffffff)
fixme:shdocvw:ClientSite_GetContainer (0xd678234)->(0x33d75c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0xd678234)->(0xb7ecc3d3)
fixme:shdocvw:ClOleCommandTarget_Exec (0xd678234)->((null) 25 0 0x33d698 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0xd678234)->((null) 26 0 0x33d698 (nil))
fixme:mshtml:HTMLTextContainer_get_scrollWidth (0xeb93344)->(0xb5246e0)
fixme:mshtml:HTMLTextContainer_get_scrollHeight (0xeb93344)->(0xb5246e4)
fixme:mshtml:HTMLTextContainer_get_scrollWidth (0xeb93344)->(0xb5246e0)
fixme:mshtml:HTMLTextContainer_get_scrollHeight (0xeb93344)->(0xb5246e4)
fixme:mshtml:HTMLTextContainer_get_scrollWidth (0xeb93344)->(0xb5246e0)
fixme:mshtml:HTMLTextContainer_get_scrollHeight (0xeb93344)->(0xb5246e4)
Shutting down. . .
300client callback thread error
```
and steam/cs/wine shuts down.

Google doesn't seem to find others with similar problems, thus my thread here.

Thanks in advance for any help on this, if you need any information about my system, just write it here :)

---

### Post by pihl on 2006-08-19
Hurray!
Fixed everything by putting -gl in launch options, nevermind :D
Thanks

---

### Post by .Ix on 2007-12-26
i'm just testing this because my brother wants to switch to ubuntu but wants to play CS on better resolutions.

anyway, whenever i try to run CS 1.4 in wine, only 640 x 480 shows the entire screen. higher resolutions like 800 x 600 and 1024 x768 are cropped to the upper left corner like the topic starter. 

i tried using your launcher options and adding -gl. the game starts full screen, but crashes after i pick my character model. also tried removing -gl and the heapsize option, but it still crashes. 

system specs:
pentium M 1.7ghz laptop
intel gma 855
1gb ram

---

### Post by .Ix on 2007-12-27
help please?

---

### Post by Hobbez on 2008-07-18
I had a problem with the window size of counter strike ... It was actually a pretty easy fix so I am trying to make it more available than it was for me. 

This was a helpful solution for me. When the window is small as it is for me running compviz and dual monitors. The problem I had was cs was opening in a 800 x 600 window, and there was no option to change it in steam.

The solution is to go to wine and let it manage it’s self… I also messed with the default wine window size so it would take up the whole screen (one face of my right cube.

"
Default Re: Missing option from merge? Wine fullscreen woes :(
Quote:
Originally Posted by chuckyp
I’m assuming the plugin will hit git stream soon?
In the meantime, (in Cedega) you can untick the “Managed” option, and with most games this will work and fix this problem.
"

In wine, find where you can switch the window management style and choose for wine to manage it..

HTH
-r

Here is the forum url where I found my answer.

[http://forum.compiz-fusion.org/showthread.php?t=2507](http://forum.compiz-fusion.org/showthread.php?t=2507)

The wget for the SteamInstall.exe on
[http://thepemberton.com/posts/archives/13#comment-4635](http://thepemberton.com/posts/archives/13#comment-4635)
didn’t work for me. I searched “SteamInstall.exe” in google and found a different copy. This is the one I used, and for sheer convince I have linked it here.

SteamInstall.exe is here.
[http://www.ausgamers.com/files/details/html/10694](http://www.ausgamers.com/files/details/html/10694)

---

### Post by Kareeser on 2009-04-03
Urgh... I'm still experiencing this problem on my install of counter-strike. Finally, Steam will install counter-strike on a 64-bit CPU, but then this problem hits :(

I'm stuck in perpetual 640x480 on my gorgeous 1680x1050 screen, and I'm squinting to even play :(

Edit: [Submitted a bug](http://bugs.winehq.org/show_bug.cgi?id=17944)

---

### Post by Kareeser on 2009-04-15
Update: **Problem Solved**

Because Twinview merges both monitors into one display, fullscreen games in WINE (at current, affected games seem to be games based on the Half-Life engine) won't resize to the correct resolution and default to a small 640x480 in the middle of the screen.

You need to update your xorg.conf file and add a proper metamode. See: [http://www.kareeser.com/ubuntu/metamodes.php](http://www.kareeser.com/ubuntu/metamodes.php)

---

