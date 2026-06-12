---
title: "[TUT] How To Play Tibia On Ubuntu!"
date: 2007-08-02
forum: Wine
---

### Post by sub7 on 2007-08-02
I finally have it working on feisty:

Install this older version of wine
```
http://wine.budgetdedicated.com/archive/ubuntu/dapper/wine_0.9.15~winehq0~ubuntu~6.06-1_i386.deb
```

Download Windows Tibia Client
```
https://secure.tibia.com/account/?subtopic=downloadclient
```

In the terminal type
```
cd ~/.wine/drive_c/Program\ Files/Tibia
```
and then
```
wine Tibia.exe engine 0
```

Make a launcher by opening text editor and pasting
```

#!/bin/bash
cd ~/.wine/drive_c/Program\ Files/Tibia
WINEDEBUG=-all wine Tibia.exe engine 0

```

then chmod the file to executable
```
chmod +x <name of the file that you just have created>

```

W00p!

---

### Post by Holder on 2007-08-03
THANKS!!!!!!!!!!!!
Dude, Finally i can run Tibia! I own you one ;)

---

### Post by Ripfox on 2007-08-03
Yes!! This rules, thanks dude.

---

### Post by mainieri on 2007-12-09
hey i keep gettin External Exception 8000010 whenever i try to install tibia with the old version of wine.  Why is this?

---

### Post by enricoluigi on 2008-02-22
> **mainieri said:**
> hey i keep gettin External Exception 8000010 whenever i try to install tibia with the old version of wine.  Why is this?
I had the same problem on my pc
Just install your video card's driver
Then install the tibia for linux

if doesn't work send me an mp =D

---

### Post by Cloud4Twenty on 2008-11-18
Ok so I'm new to Linux. I'm not a total tard though very close. I'm not sure what to do. I install the program and tried to cd to the right path and run it but i get an error

Cannot find file 'Z:\home\me\Tibia.dat'. (Error Code 1)

Please re-install the program

Any help would be greatly appreciated.

---

### Post by wingnux on 2008-11-18
Why use wine if there's a native Tibia client for linux and it works just fine? (it needs hw acceleration, tough)

---

### Post by DEMWilson on 2008-11-27
> **wingnux said:**
> Why use wine if there's a native Tibia client for linux and it works just fine? (it needs hw acceleration, tough)

I use wine because my hardware doesn't support openGL which is what you have to run to use the linux tibia client.

@thread: Thank you so much, I can finally play. ^^

---

### Post by cogadh on 2008-11-28
:confused:
That makes no sense. Your hardware must support OpenGL because that is what Wine uses to render graphics (it translates DirectX to OpenGL). Not to mention, all modern video cards support OpenGL, as long as you have the correct drivers installed. Unless you have a really, *really* old graphics card, you should be able to use the Linux native Tibia client. If you are happy with running it through Wine, I suppose that doesn't matter, though.

---

### Post by Cloud4Twenty on 2008-12-24
So after playing around and re installing / un installing over and over again I finally get it to open....... well the windows version through wine at least, but the client is all sorts of messed up, I can't click anything. I tried the Tibia client for Linux and that one doesn't even run, it starts then immediately closes and does nothing at all, I guess it could be my drivers but then at that point.. how do I install any updated drivers? Remember I'm new, please be gentle. More Info: I have a some what older Dell Inspiron E1505 from like 2006 if that helps

---

### Post by Cloud4Twenty on 2009-01-23
Ok so I guess no one knows how to help me.. I've tried everything i can find to get Tibia working, and all I get is 
Tibia Error

Cannot find file 'Tibia.dat'. (Error Code 1)

Please re-install the program.

I don't know what to do anymore, I'd hate to have to go back to windows over some friggin game. Well if no one can help me to get Tibia working can someone tell me of a comparable MMO thats free??

Oh yea I also tried WINE, the window opens but can't do anything with it, and Runesape has been WE-TODD-DID ever since they got rid of Classic, or TRUE RUNESAPE!! Please Help.

---

### Post by Cloud4Twenty on 2009-01-25
Not sure if this helps at all but when I tried to run it through WINE I get this in terminal

fixme:win:EnumDisplayDevicesW ((null),0,0x32e778,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:ddraw:IDirectDrawImpl_QueryInterface (0x158068) The App is requesting a D3D device, but a non-OpenGL surface type was choosen. Prepare for trouble!
err:ddraw:IDirectDrawImpl_QueryInterface  (0x158068) You may want to contact wine-devel for help
err:ddraw:IDirectDrawSurfaceImpl_QueryInterface No interface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface

Not sure what it is but figured if I posted it someone might be able to help me >.<

Once again this was when I tried through WINE, the native error I was getting I posted before if anyone can help with either , thank you

---

### Post by amcguinn on 2010-05-16
I know this is a year old, but I had the same problem as Cloud4Twenty; the solution is at [WineHQ]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=10803&iTestingId=29271") : set the following in ~/.wine/user.reg:

[Software\\Wine\\Direct3D] 1205188874
"DirectDrawRenderer"="gdi"
"Multisampling"="enabled"
"OffscreenRenderingMode"="fbo"
"PixelShaderMode"="enabled"
"RenderTargetLockMode"="textex"
"UseGLSL"="disabled"
"VertexShaderMode"="hardware"

---

### Post by gewone on 2012-03-10
I know there is an official Linux client by now.
It works pretty great, also.
However, I can't seem to make a desktop shortcut/launcher! :/
It simply won't launch, and I don't know how to debug.

Ideas?

**EDIT:**
Sorry, I didn't realize this thread was sub-categorized under Wine! :/

---

