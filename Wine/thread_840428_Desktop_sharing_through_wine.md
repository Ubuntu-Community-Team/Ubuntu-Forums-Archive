---
title: "Desktop sharing through wine"
date: 2008-06-25
forum: Wine
---

### Post by InfernalNeutrino on 2008-06-25
Hi,

The situation is as follows. I work in a research group which often utilizes video conferences to keep in touch with each other, and quite frequently various members of the group use desktop sharing software to show data, slides, or whatever it is that is being discussed. That is where the fun begins.

Everyone (except me of course :) ) is a windows user, and the desktop sharing software of choice for them is something called Bridgit [(clicky)]("http://www2.smarttech.com/st/en-US/Products/Bridgit/"). The short story is that you download and run an executable called Bridgit.exe, which contains the whole desktop sharing program. Now, this software explicitly supports only windows or mac, and requires IE5 or "better" for the windows version. I decided to try to get it running through wine. I successfully installed wine and IE6 on my laptop, which is running Xubuntu 8.04 64 bit. I've been playing around with fluxbox, but I doubt that my desktop environment choice should be playing a role. I am using wine-1.0.

So, I downloaded the executable, and ran it. Here is what my terminal looks like:

$ wine Bridgit.exe 
fixme:wininet:InternetAttemptConnect Stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33f074,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x33f074,0x00000000), stub!
fixme:wininet:FindNextUrlCacheEntryW (0x140620, 0xa63c68, 0x33faa8) stub
fixme:gdiplus:GdipBitmapGetPixel not implemented
wine: Call from 0x7b844c50 to unimplemented function gdiplus.dll.GdipBitmapSetPixel, aborting

I tried alternating the OS setting between XP, Vista, and 2008 with no luck (I get the same messages no matter which I use). I guess what I would appreciate is a translation of the error messages, since I am new to wine (as in I started using it today) and have some learning to do about how it works. Any input on what the messages mean and what could be causing it would be greatly appreciated. Thanks!

---

### Post by dankegel on 2008-12-01
Sure, Wine hasn't implemented GdipBitmapSetPixel yet, that's 
[http://bugs.winehq.org/show_bug.cgi?id=10982](http://bugs.winehq.org/show_bug.cgi?id=10982)

You can work around this with
  wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks)
  sh winetricks gdiplus

---

### Post by Brynster on 2008-12-01
can they not just use the Smart board software. 

[http://www2.smarttech.com/st/en-US/Support/Downloads/SBS/SBSv97Linux.htm](http://www2.smarttech.com/st/en-US/Support/Downloads/SBS/SBSv97Linux.htm)

If i remember correctly this allowed direct access to each others work in progress. I may be wrong its about 5-6 years ago that i sold SmartBoards and there software

---

