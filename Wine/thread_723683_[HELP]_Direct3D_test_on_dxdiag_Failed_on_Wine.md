---
title: "[HELP] Direct3D test on dxdiag Failed on Wine"
date: 2008-03-13
forum: Wine
---

### Post by bhocay on 2008-03-13
hi.. i've finished installing directx 9.0 on wine with the native and builtin stuff.

some question in mind:
1. i got tested the DirectDraw and it was oke.. but when i test the Direct3D, it was crashed out with a white screen and back to prompt..

2. does my wine doesnt support direct3d? cozz on regedit i didnt see any Direct3d on wine..

3. i try to playing RF online(Rising Force) the launcher on game load an error:
cannot play with the VGA (MaxVertexBlendMatricex:0)

for vga driver info:

-> fglrxinfo:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.1.7412 Release

-> glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: ATI Technologies Inc.

direct rendering:yes
-> glxinfo | grep ATI   
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
    GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, 
    GL_ATI_meminfo, GL_ATI_separate_stencil, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 

SomeBody help me pliss :(  Thank you

---

### Post by gsmanners on 2008-03-13
Direct X is too low level to work properly in Wine. You'll just have to wait for built-in support if you want DX9.

---

### Post by bhocay on 2008-03-13
[http://wine-review.blogspot.com/2007/11/directx-90c-on-linux-with-wine.html](http://wine-review.blogspot.com/2007/11/directx-90c-on-linux-with-wine.html)

is this a fake?

cozz my dxdiag crashed when just testing Direct3D 7

---

### Post by gsmanners on 2008-03-14
It's not per se "fake," but there is a disclaimer at the bottom.

> Keep in mind d3d8, d3d9, ddraw will only work as builtin, and in most cases you should try to use builtin dsound and dinput. I have had limited success with (dsound and dinput) in native Windows mode btw... The reason why these dlls have to be used in builtin mode is there need for direct access to your hardware. direct music and direct play can be used in native windows mode in most circumstances.

---

### Post by bhocay on 2008-03-14
i've tried to change the native & build in on d3d8, d3d9, nd ddraw.. but it seems.. doesnt effect the diags..

was it because of my display driver sets? or  the wine didnt support the Direct3D

coz if i run warcraft 3 without the opengl mode then the performance goes crap

---

### Post by Suthern on 2008-04-24
Has anyone solved this? I'm getting the same issues with wine 0.9.59 on Ubuntu 7.10, with the latest ati drivers.

---

### Post by oldneuro on 2008-05-28
I am running ubuntu 8.04, using FGLRX driver for my ATI 300x video card, compiz and gl_gears works great, Installed WINE and DirectX 9, properly setting the native/builtin dll preferences, and dxdiag crashes for me on loading Direct3D.

One thing I noticed is that when I type glxinfo, it defaults to display 1:0 (which does not have Direct Rendering) as opposed to 0:0 (which does have Direct Rendering), but glxinfo -display 0 shows direct rendering enabled.

Please help

---

