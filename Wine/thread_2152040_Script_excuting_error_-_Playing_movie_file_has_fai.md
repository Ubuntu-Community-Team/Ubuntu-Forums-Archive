---
title: "Script excuting error - Playing movie file has failed (Yume Miru Kusuri)"
date: 2013-06-06
forum: Wine
---

### Post by Sovasin on 2013-06-06
Hello.

I've recently installed a [visual novel]("https://en.wikipedia.org/wiki/Visual_novel") called [Yume Miru Kusuri]("https://en.wikipedia.org/wiki/Yume_Miru_Kusuri") using wine. The game itself works fine; however, I can't seem to be able to view the opening cinematic (a .dat file). I always get the error "Script excuting error - Playing movie file has failed" when I launch the game. Pressing OK brings me to the title screen and everything goes smoothly from there. However, I know there's a cinematic at the end of the game and I'm pretty sure I'll get the same error when I try to view it; haven't tried that yet.

I can view the cinematics manually by going into the game files and opening the .dat files using Videos. I can't seem to view them in-game however.

Here's the data from the terminal when the error occurs.

[email]saurav@Saurav-LAPTOP:~/.wine[/email]/drive_c/Program Files/yume miru kusuri$ wine yumemiru.exe
fixme:win:WINNLSEnableIME hwnd 0x10060 enable 0: stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f590,0x00000000), stub!
fixme:amstream:IAMMultiMediaStreamImpl_AddMediaStream (0x285d378/0x285d378)->(0x13bb58,{a35ff56a-9fda-11d0-8fdf-00c04fd9189d},0,(nil)) partial stub!
fixme:amstream:IAMMultiMediaStreamImpl_AddMediaStream (0x285d378/0x285d378)->((nil),{a35ff56b-9fda-11d0-8fdf-00c04fd9189d},1,(nil)) partial stub!
fixme:amstream:IDirectDrawMediaStreamImpl_CreateSample (0x2864a08)->((nil),(nil),0,0x610ea0) stub!

Here's a screenshot.

[IMG]http://img826.imageshack.us/img826/515/screenshotfrom201306070.png[/IMG]

(I launched the game twice; the code above "saurav@Saurav-LAPTOP:~/.wine/drive_c blah blah blah" came up when launching the game for the first time, then closing it.)
My computer is capable of playing the cinematics; I can do so by manually opening them. I have no idea why I can't play the cinematics on wine however.

I'm a bit of a beginner to Ubuntu so any help would be appreciated.

(I'll only be able to reply tomorrow; sorry!)

---

### Post by Sovasin on 2013-06-08
Any ideas? This isn't a huge problem since I can just view the cinematics manually by opening them from the install directory. It would be awesome to view them ingame though.

---

