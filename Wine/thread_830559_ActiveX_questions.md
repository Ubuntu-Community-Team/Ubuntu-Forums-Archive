---
title: "ActiveX questions"
date: 2008-06-15
forum: Wine
---

### Post by Zeikcied on 2008-06-15
I have some questions about ActiveX and Wine.

1. Will Wine ever duplicate ActiveX?

2. There is a suggested method of using ActiveX, and that is the Mozilla ActiveX Control.  It seems to only work with Firefox 1.5 and lower.  I found Firefox 1.5.12, and I attempted to install two of the plug-ins offered on the site.  But it didn't allow Firefox to use ActiveX, and it also didn't allow a program that requires ActiveX to run.  How should you properly install this plug-in?

3. Does the Mozilla ActiveX Control method enable ActiveX for programs that do not have a browser embedded?  The program I'm trying to get working uses eLicense to validate a legit copy.  I don't know if eLicense uses a browser, as no browser window ever displays.  But it does use ActiveX.

I can get it to work properly using ies4linux, but a few versions of Wine ago (prior to the first 1.0 release candidate), the program broke, and I can't submit a Wine bug report since I use ies4linux to run it.  So I could use some help in making ActiveX work so I can hopefully make a bug report and get it fixed.

---

### Post by cogadh on 2008-06-16
1. I don't think so

2. You don't actually need Firefox to use the control (assuming the app isn't actually browser based), you just need to install it and register the DLL in Wine:[list]
[*]Download the Mozilla ActiveX control from  downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz
[*]Extract it to ~/.wine/drive_c/Program\ Files/mozcontrol
[*]Now open a terminal,  cd to the mozcontrol directory, and run "wine regsvr32 mozctlx.dll"[/list]
3. See #2

---

### Post by Zeikcied on 2008-06-16
> **cogadh said:**
> 1. I don't think so

2. You don't actually need Firefox to use the control (assuming the app isn't actually browser based), you just need to install it and register the DLL in Wine:[list]
[*]Download the Mozilla ActiveX control from  downloads.transgaming.com/mozilla_control_downloads/mozcontrol.tgz
[*]Extract it to ~/.wine/drive_c/Program\ Files/mozcontrol
[*]Now open a terminal,  cd to the mozcontrol directory, and run "wine regsvr32 mozctlx.dll"[/list]
3. See #2
Okay, I did that.  It doesn't work.  I get:

```
Run-time error '429':

ActiveX component can't create object
```

It's a program written in VB6, if that makes any difference.  I did install the VB6 SP6 runtime, which was needed to even get to that point.

ies4linux was able to get past the ActiveX requirement.  But as I said, recent Wine versions broke the program.  (It crashes while running, but after the ActiveX part in ies4linux.)

---

### Post by larytet on 2009-01-18
In general 
try to run from command line

```

wine 'c:\\Program files\\B_G_S_S\\B_G_S_S.exe'

```

Pay attention to the double slash
You will get output like
```

fixme:ole:OleLoadPictureEx (0xaeed4c,365564,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32fae8), partially implemented.
fixme:ole:OleLoadPictureEx (0xaeed4c,1086,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32fae8), partially implemented.
fixme:ole:OleLoadPictureEx (0xaeed4c,774,1,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=0,y=0,f=0,0x32fae8), partially implemented.
fixme:ole:OleLoadPictureEx (0xaeed4c,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0xd06c90), partially implemented.
fixme:ole:OleLoadPictureEx (0xaeed4c,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0xd06d08), partially implemented.
fixme:ole:OleLoadPictureEx (0xaeed4c,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0xd06d80), partially implemented.
fixme:ole:OleLoadPictureEx (0xaeed4c,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0xd06df8), partially implemented.
fixme:ole:OleLoadPictureEx (0xaeed4c,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0xd06e70), partially implemented.
fixme:ole:OleLoadPictureEx (0xaeed4c,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0xd06ee8), partially implemented.
fixme:ole:OleLoadPictureEx (0xaeed4c,0,0,{7bf80980-bf32-101a-8bbb-00aa00300cab},x=32,y=32,f=0,0xd06f60), partially implemented.
fixme:ole:OLEPictureImpl_SaveAsFile (0xd00028)->(0xd17100, 0, (nil)), hacked stub.
err:ole:CoGetClassObject class {00000514-0000-0010-8000-00aa006d2ea4} not registered
err:ole:create_server class {00000514-0000-0010-8000-00aa006d2ea4} not registered
err:ole:CoGetClassObject no class object {00000514-0000-0010-8000-00aa006d2ea4} could be created for context 0x5

```
OLEPictureImpl is the key to the required DLL. In this case probably msscript.ocx. You can try to copy missing DLL to ~/.wine/drive_c/windows/system32/ and run 
```

:~/lectures/mishak/B_G_S_S_setup$ regsvr32 msscript.ocx
Successfully registered DLL msscript.ocx

```
Also folder c:\windows\Fonts is missing frequently

---

