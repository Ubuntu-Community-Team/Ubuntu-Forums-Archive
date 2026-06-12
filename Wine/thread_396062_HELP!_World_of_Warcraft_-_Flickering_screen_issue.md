---
title: "HELP! World of Warcraft - Flickering screen issue"
date: 2007-03-29
forum: Wine
---

### Post by stomponthis on 2007-03-29
Hi all,

First post.... long time post reader! I need some help! :P

I am trying to run WOW with wine in Ubuntu 6.10 the Edgy Eft!
I have installed my Nvidia graphis card with help from a HOW TO from Ubuntu forums, copied my whole WOW directory from windows in my fake C drive and have got wow to run now.
My problem is when i run WOW it flickers like theres no tomorrow and on the log in screen there is no background picture. Basically just display issues.
I think my graphics card is installed right, I directaly followed a another HOW TO guide for that.

Any help would be greatly appreciated :P and if you need any more information to help me with my problem just ask :P

Below is the info from the terminal when I run WOW

THANKS HEAPS EVERY1!!!

thomas@thomas-desktop:~$ wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe --opengl
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33edd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f33c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f544,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33f04c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wgl:X11DRV_wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:imm:ImmAssociateContextEx (0x10024, (nil), 16): stub

---

### Post by hikaricore on 2007-03-29
There should only be one "-" before opengl like this:

```
wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe -opengl
```

Otherwise you're not running in opengl mode.

Don't know if this is the problem but it could be.

Also the terminal output is mostly normal.

---

### Post by stomponthis on 2007-03-29
Hey and thanks for the post on my problem.
I tried running again removing the extra "-"   but doesnt seem to help!


I have now almost got it running, I only get the glitch in the display when in the game, no longer on the opening log in screen.
There is an error from the terminal 

err:wgl:X11DRV_wglGetPixelFormatAttribivARB Unable to convert iPixelFormat 0 to a GLX one, expect problems!

which I think is the problem.
I added the "opengl" switch in the /WTF/Config.wtf file along with a few others that seem to be getting me further


Any help would be appreciated

---

### Post by stomponthis on 2007-03-30
Hello again all, 

First of all fixed the problem, it was the graphics card driver that led me wrong. I used the driver from the website and installed myself, rather then a command "aptitude" which i used before. Dnt quite know the difference but I have fixed nothing else since my problem and it works fine now.

I knw every1s sick of WOW threads, but now I'm an ubuntu user through and through, no  need for windows now as I have my games!

NOT MANY CUPS OF UBUNTU YET BUT GETN BETTER!!!!! AND IM HERE TO STAY


stomponthis ----> SLAM'S THE DOOR ON WINDOWS, DELETED XP!

---

### Post by caedz on 2007-04-03
How is your WOW running after applying the latest patch?

---

### Post by Chaositect on 2008-05-01
> **caedz said:**
> How is your WOW running after applying the latest patch?

My upgrade to Hardy Heron went smoothly for the most part, and now EVE (under cedega) is running better than before, but WOW has a screen flicker from the first load screen.

I also re-installed my newer ATI X1950 Pro video card after the upgrade(used the Ge-force 8200 previously due to many different graphics issues though Hardy Heron handled the card expertly and the only issue I have is WOW.)

The initial loadup screen also comes up with an 'unable to find URL' and the background is white.  When I press "play" the text screens are normal, but the background is black with a fliker about once a second (behind the flicker is my desktop)  I can go all the way into the game like this, but the game screen is similar with forground items (icons, mini map frame, etc) showing properly, but the background is all white with only a circle around my selected character and a shadow...

I've also had an issue with the in game data not saving...  had to re-set all variables every log in.  I've been dealing with it, too lazy to find an answer, but it's getting annoying =)


Thanks for the help!

AMD 64 bit 3200+ processer 2GB ram

-M

---

### Post by ribbon on 2008-05-03
I'm having this issue as well. Just installed ubuntu for the first time  (64bit), I'm playing under wine and my video card is ati 1900xt. I used envyNG to install my graphics drivers.

At first I was getting flickerinng and strange polygons/artifacts and black login screen, but I fixed all of the latter by modifying my config.wtf, but still can't figure out how to get rid if flickering...

EDIT: Fixed it by doing System > Preferences > Appearance > None

Too bad, no compiz and wow ;[

---

### Post by Chaositect on 2008-05-03
Thanks for the update Ribbon.  I got my config.wtf and my xorg.conf in line, and that fixed the rest.  I hadn't figured out the flickering till you mentioned it.

Now to wait till wine 9.60 update to fix the shift click issues, and study a bit to find fix to profile data not saving...

Very playable now though.  Thanks!

:)

---

