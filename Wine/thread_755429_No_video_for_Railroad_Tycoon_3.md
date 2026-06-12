---
title: "No video for Railroad Tycoon 3"
date: 2008-04-14
forum: Wine
---

### Post by alex.dason on 2008-04-14
I'm trying to run Railroad Tycoon 3 in 0.9.59.

I am able to get sound and the game works [because I can click around and it does things], but there is zero video. After a while the screen will change from all black to the fuzz you get on your tv when nothing is connected.

Here is the terminal output [it doesn't make any sense to me]:

```
alex@.../Railroad Tycoon 3$ wine rt3.exe
fixme:spoolsv:serv_main (0 (nil))
fixme:win:EnumDisplayDevicesW ((null),0,0x33f8d4,0x00000000), stub!
fixme:d3d:test_pbo_functionality >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Loading the PBO test texture
 @ directx.c / 3413
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:d3d8:ValidatePixelShader (0x1a2f9b0 (nil) 0 (nil)): stub
fixme:d3d8:ValidatePixelShader (0x1a2fb70 (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0x1a9acd8 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0x1a2fcc8 (nil) (nil) 0 (nil)): stub
fixme:d3d8:ValidateVertexShader (0x1a2fc00 (nil) (nil) 0 (nil)): stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x12e000) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x12e000) : stub

```

My video card is ATI Radeon X1600, with the latest proprietary drivers from ATI.

Any help is appreciated.

---

