---
title: "Guild Wars problems with 1.0-rc5 and 8.04"
date: 2008-06-14
forum: Wine
---

### Post by devosion on 2008-06-14
Im beginning to think my nvidia proprietary driver doesnt work properly in 8.04 but i'll detail the problems im experiencing first and get some ideas before I do anything to rash.

In any case GW will load and get me to the title and character selection screens, through win98 and win2000, but soon as I try to load up I receive the following trailing line errors.

> fixme:d3d:ActivateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer @ context.c / 1077
fixme:d3d_surface:flush_to_framebuffer_drawpixels >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer(myDevice->offscreenBuffer) @ surface.c / 1175
fixme:d3d_surface:flush_to_framebuffer_drawpixels >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glDrawBuffer(myDevice->offscreenBuffer) @ surface.c / 1253
err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.


When I was running Guild Wars on 7.10 I never had a problem like this, and I was using wine 0.9.58. I am also receiving a very strange fixme error when starting up GW. 

> fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers


These fixme's are succeeded by thousands of lines of d3d and dxdiag fixme's. Im not quite sure what the problem is but im beginning to suspect it is my video card driver. Im using an NVIDIA 8500gt. Please help.

---

### Post by tao2queue on 2008-07-09
I don't know if you've made any progress with this at all, please advise if you have.
I've noticed the same thing you have; Guild Wars emulation on Ubuntu 8.04 just isn't as good as it is on Ubuntu 7.10. I'm still rying to figure out where the root of this issue is, but its not the WINE versions its something in 8.04

---

