---
title: "Unable to start installed program"
date: 2017-02-07
forum: Wine
---

### Post by peter1897 on 2017-02-07
I installed [xlaunchpad]("http://www.xwidget.com/") using wine but when i try to start it i get 'program error'. But if i click the button 'show details' it freezes on 'loading detailed information... please wait'. How to find why the program can't start?

---

### Post by leunam12 on 2017-02-07
start it from the terminal ```
wine /path/to/program.exe
```

---

### Post by peter1897 on 2017-02-07
This is what i get when i start it from terminal but i don't know what these messages mean:
```
osboxes@osboxes:~/.wine/drive_c/Program Files/XLaunchPad$ wine XLaunchPadStarter.exe 
osboxes@osboxes:~/.wine/drive_c/Program Files/XLaunchPad$ fixme:d3d:wined3d_guess_card No card selector available for card vendor 0000 (using GL_RENDERER "Gallium 0.4 on llvmpipe (LLVM 3.8, 256 bits)").
fixme:win:EnumDisplayDevicesW ((null),0,0x33f988,0x00000000), stub!
err:d3d:context_create Failed to set pixel format 29 on device context 0x50048.
err:d3d:context_create Failed to set pixel format 36 on device context 0xb0033.
fixme:d3d:wined3d_get_format Can't find format WINED3DFMT_R24_UNORM_X8_TYPELESS (0x49) in the format lookup table
fixme:d3d:getDepthStencilBits Unsupported depth/stencil format WINED3DFMT_UNKNOWN.
err:d3d:context_create Failed to set pixel format 5 on device context 0x1006c.
err:d3d:context_create Failed to set pixel format 13 on device context 0x1006e.
err:d3d:context_choose_pixel_format Can't find a suitable iPixelFormat
err:d3d:context_create Failed to set pixel format 13 on device context 0x10070.
err:d3d:context_create Failed to set pixel format 29 on device context 0x10072.
err:d3d:context_create Failed to set pixel format 36 on device context 0x10074.
fixme:d3d:wined3d_get_format Can't find format WINED3DFMT_R24_UNORM_X8_TYPELESS (0x49) in the format lookup table
fixme:d3d:getDepthStencilBits Unsupported depth/stencil format WINED3DFMT_UNKNOWN.
err:d3d:context_create Failed to set pixel format 5 on device context 0x10076.
err:d3d:context_create Failed to set pixel format 13 on device context 0x10078.
err:d3d:context_choose_pixel_format Can't find a suitable iPixelFormat
err:d3d:context_create Failed to set pixel format 13 on device context 0x1007a.
wine: Unhandled page fault on read access to 0x00a9337c at address 0x6bf8c284:0x00403fba (thread 002c), starting debugger...
```

---

