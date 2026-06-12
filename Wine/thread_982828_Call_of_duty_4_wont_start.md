---
title: "Call of duty 4 wont start"
date: 2008-11-15
forum: Wine
---

### Post by Trap3d on 2008-11-15
id like to run cod4 but when i wine iw3sp.exe i get thrown out of the game and heres what the console says:

```
trap3d@trap3d-desktop:~$ cd ~/.wine/drive_c/Program\ Files/Activision/Call\ of\ Duty\ 4\ -\ Modern\ Warfare/ && wine iw3sp.exe
fixme:win:EnumDisplayDevicesW ((null),0,0x32f8e4,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:IWineD3DVolumeImpl_LockBox (0xc615100) : pBox=(nil) stub
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2559
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2559
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2559
fixme:d3d:tex_bumpenvmat >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvfv(GL_TEXTURE_SHADER_NV, GL_OFFSET_TEXTURE_MATRIX_NV, mat) @ state.c / 2559
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #2: "0(5) : warning C7551: OpenGL first class arrays require #version 120\n"
fixme:d3d_shader:print_glsl_info_log Error received from GLSL shader #3: "Vertex info\n-----------\n0(5) : warning C7551: OpenGL first class arrays require #version 120\n"
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d:CreateContext >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glTexEnvi(GL_TEXTURE_SHADER_NV, GL_PREVIOUS_TEXTURE_INPUT_NV, ...
 @ context.c / 517
fixme:d3d9:IDirect3DDevice9Impl_CreateIndexBuffer (0x165ee8) call to IWineD3DDevice_CreateIndexBuffer failed
fixme:d3d9:IDirect3DDevice9Impl_CreateSurface (0x165ee8) call to IWineD3DDevice_CreateSurface failed
fixme:d3d9:D3D9CB_CreateSurface (0x165ee8) IDirect3DDevice9_CreateSurface failed
fixme:d3d:IWineD3DDeviceImpl_CreateTexture Failed to create surface  0x12b247a0
fixme:d3d9:IDirect3DDevice9Impl_CreateTexture (0x165ee8) call to IWineD3DDevice_CreateTexture failed
Segmentation fault
trap3d@trap3d-desktop:~/.wine/drive_c/Program Files/Activision/Call of Duty 4 - Modern Warfare$ 

```
hope someone can get sumn out of there....

---

