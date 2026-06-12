---
title: "C&amp;C Generals in Wine? Error message"
date: 2008-04-08
forum: Wine
---

### Post by russ18uk on 2008-04-08
Hi, is there any fix seen for this?

```
russ@wtf:~$ wine "c:/Games/Command & Conquer Generals Zero Hour/generals.exe"
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:cursor:CURSORICON_LoadFromFile No support for .ani cursors.
fixme:win:EnumDisplayDevicesW ((null),0,0x348844,0x00000000), stub!
fixme:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain The app requests more than one back buffer, this can't be supported properly. Please configure the application to use double buffering(=1 back buffer) if possible
[B]err:d3d:getColorBits Unsupported format: WINED3DFMT_A8
err:d3d:getColorBits Unsupported format: WINED3DFMT_L8
err:d3d:getColorBits Unsupported format: WINED3DFMT_A8L8
err:d3d:getColorBits Unsupported format: WINED3DFMT_A4L4[/B]
err:ole:CoGetClassObject class {2b2cc8b0-2dc0-48c6-b6fd-c07820a6477e} not registered
err:ole:CoGetClassObject class {2b2cc8b0-2dc0-48c6-b6fd-c07820a6477e} not registered
err:ole:create_server class {2b2cc8b0-2dc0-48c6-b6fd-c07820a6477e} not registered
err:ole:CoGetClassObject no class object {2b2cc8b0-2dc0-48c6-b6fd-c07820a6477e} could be created for context 0x7
fixme:imm:ImmGetDefaultIMEWnd (0x330048 - (nil) 0x23ff8b0 ): semi-stub
fixme:d3d8:ValidatePixelShader (0x2ff34d0 (nil) 0 (nil)): stub
fixme:d3d8:ValidatePixelShader (0x2a258b0 (nil) 0 (nil)): stub
fixme:d3d8:ValidatePixelShader (0x2ff34d0 (nil) 0 (nil)): stub
fixme:imm:ImmReleaseContext (0x330048, 0x23ff8b0): stub
russ@wtf:~$ 
```

Not sure if there is a way to force double buffering in Generals/ZH so if anyone knows I'd be greatful :guitar:

---

### Post by insineratehymn on 2008-04-08
Two things:

Have you tried this:
[http://appdb.winehq.org/appview.php?iVersionId=1717](http://appdb.winehq.org/appview.php?iVersionId=1717)

If so, what version of wine are you running?

---

### Post by russ18uk on 2008-04-09
Hi, thanks for that site - seems very useful. Wine version is 0.9.58 and I have successfully started WoW, NVIDIA's Dawn demo, and ATI's Pipe Dream and Chimp demos so shaders are working and everything seems OK. Not able to run 3D Mark to see any speed differences. ZH and Generals are up to date since I play online. Will report back the findings tomorrow. Thanks for the reply :)

---

### Post by benste on 2008-12-29
Nothing new?

---

