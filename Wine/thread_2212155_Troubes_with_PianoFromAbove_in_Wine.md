---
title: "Troubes with PianoFromAbove in Wine"
date: 2014-03-19
forum: Wine
---

### Post by stu-klaum.tiernan on 2014-03-19
Hello everybody. I am trying to get this program called PianoFromAbove to work in wine.
PianoFromAbove is a highly cusomizable midi player and vizualizer. see the video!
[http://www.youtube.com/watch?v=ISd4Lp74MGk](http://www.youtube.com/watch?v=ISd4Lp74MGk)
Anyway, the program starts up just fine, but when the black box that shoes the notes and piano loads, up its just black. I dont see any notes or anything.
I tried running it under the terminal, figruring it had something to do with DirectX, since thats what PianoFromAbove uses. But when I started it up, I couldn't make
sense of any of the error messages Wine spat out at me. Maybe you guys could make sense of it? :confused:

Here are the error messages:

fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16B16A16_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:win:EnumDisplayDevicesW ((null),0,0x9ee51c,0x00000000), stub!
fixme:d3dx:D3DXCreateFontIndirectW (0x151d28, 0x9ee918, 0x64c72c): stub
fixme:d3dx:D3DXCreateFontIndirectW (0x151d28, 0x9ee918, 0x64c730): stub
fixme:d3dx:D3DXCreateFontIndirectW (0x151d28, 0x9ee918, 0x64c734): stub
fixme:d3dx:D3DXCreateFontIndirectW (0x151d28, 0x9ee918, 0x64c738): stub
fixme:d3dx:D3DXCreateFontIndirectW (0x151d28, 0x9ee918, 0x64c73c): stub
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3dx:ID3DXFontImpl_OnResetDevice (0x1c18f8)->(): stub
fixme:d3dx:ID3DXFontImpl_OnResetDevice (0x1c2ff8)->(): stub
fixme:d3dx:ID3DXFontImpl_OnResetDevice (0x1c1658)->(): stub
fixme:d3dx:ID3DXFontImpl_OnResetDevice (0x1c5ce0)->(): stub
fixme:d3dx:ID3DXFontImpl_OnResetDevice (0x1c7200)->(): stub
fixme:d3dx:ID3DXFontImpl_OnLostDevice (0x1c18f8)->(): stub
fixme:d3dx:ID3DXFontImpl_OnLostDevice (0x1c2ff8)->(): stub
fixme:d3dx:ID3DXFontImpl_OnLostDevice (0x1c1658)->(): stub
fixme:d3dx:ID3DXFontImpl_OnLostDevice (0x1c5ce0)->(): stub
fixme:d3dx:ID3DXFontImpl_OnLostDevice (0x1c7200)->(): stub
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3dx:ID3DXFontImpl_OnResetDevice (0x1c18f8)->(): stub
fixme:d3dx:ID3DXFontImpl_OnResetDevice (0x1c2ff8)->(): stub
fixme:d3dx:ID3DXFontImpl_OnResetDevice (0x1c1658)->(): stub
fixme:d3dx:ID3DXFontImpl_OnResetDevice (0x1c5ce0)->(): stub
fixme:d3dx:ID3DXFontImpl_OnResetDevice (0x1c7200)->(): stub
fixme:d3dx:ID3DXFontImpl_OnLostDevice (0x1c18f8)->(): stub
fixme:d3dx:ID3DXFontImpl_OnLostDevice (0x1c2ff8)->(): stub
fixme:d3dx:ID3DXFontImpl_OnLostDevice (0x1c1658)->(): stub
fixme:d3dx:ID3DXFontImpl_OnLostDevice (0x1c5ce0)->(): stub
fixme:d3dx:ID3DXFontImpl_OnLostDevice (0x1c7200)->(): stub
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3dx:ID3DXFontImpl_OnResetDevice (0x1c18f8)->(): stub
fixme:d3dx:ID3DXFontImpl_OnResetDevice (0x1c2ff8)->(): stub
fixme:d3dx:ID3DXFontImpl_OnResetDevice (0x1c1658)->(): stub
fixme:d3dx:ID3DXFontImpl_OnResetDevice (0x1c5ce0)->(): stub
fixme:d3dx:ID3DXFontImpl_OnResetDevice (0x1c7200)->(): stub
fixme:d3dx:ID3DXFontImpl_OnLostDevice (0x1c18f8)->(): stub
fixme:d3dx:ID3DXFontImpl_OnLostDevice (0x1c2ff8)->(): stub
fixme:d3dx:ID3DXFontImpl_OnLostDevice (0x1c1658)->(): stub
fixme:d3dx:ID3DXFontImpl_OnLostDevice (0x1c5ce0)->(): stub
fixme:d3dx:ID3DXFontImpl_OnLostDevice (0x1c7200)->(): stub
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3dx:ID3DXFontImpl_OnResetDevice (0x1c18f8)->(): stub
fixme:d3dx:ID3DXFontImpl_OnResetDevice (0x1c2ff8)->(): stub
fixme:d3dx:ID3DXFontImpl_OnResetDevice (0x1c1658)->(): stub
fixme:d3dx:ID3DXFontImpl_OnResetDevice (0x1c5ce0)->(): stub
fixme:d3dx:ID3DXFontImpl_OnResetDevice (0x1c7200)->(): stub
fixme:d3d:wined3d_buffer_preload Too many declaration changes or converting dynamic buffer, stopping converting

BTW, I'm running Linux Mint 14 Cinnamon Edition 64-Bit running wwine 1.4.1

---

### Post by stu-klaum.tiernan on 2014-03-19
Please excuse emoticons in error messages

---

### Post by Iowan on 2014-03-19
Disabled them for you. :)

---

### Post by stu-klaum.tiernan on 2014-03-21
Please Guys! I relly need your help with this! Reply already!

---

