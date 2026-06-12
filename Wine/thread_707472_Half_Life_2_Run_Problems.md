---
title: "Half Life 2 Run Problems"
date: 2008-02-25
forum: Wine
---

### Post by rebirthflame on 2008-02-25
I recently moved to linux and have been trying to get some games to work, i looked at the appdb list for wine and saw that hl2 was rated as platinum an easy game for me to start off on i thought, anyway that hasnt happened.

I installed steam fine, installed hl2 from steam fine, started up hl2 and it gets to the start screen (new game, load game etc) but the graphics  are all messed up a screenshot is below

[http://i94.photobucket.com/albums/l102/rebirthflame21/Screenshot.png](http://i94.photobucket.com/albums/l102/rebirthflame21/Screenshot.png)

when i start the game the intial video has no textures on the eyes or the inside of the mouth they are just black and it crashes after about 30 secs

i am running the latest version of wine (0.9.55)

Terminal output

```
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6cda60) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce82970) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6e4ea0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1cea8c08) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e730870) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e7536d0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e73c290) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e747cb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e736580) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e683ef8) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e781f50) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6df190) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e72ab60) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e781f50) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6e4ea0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e683ef8) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ebfaaf0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e75f0f0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e75f0f0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e75f0f0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce51cd8) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce63408) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ebfaaf0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce82970) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6cda60) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6df190) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1cea8c08) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e73c290) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e7536d0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e747cb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e736580) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e730870) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e75f0f0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e72ab60) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce63408) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce51cd8) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6cda60) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce82970) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6e4ea0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1cea8c08) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e730870) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e7536d0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e73c290) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e747cb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e736580) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e683ef8) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e781f50) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6df190) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e72ab60) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e781f50) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6e4ea0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e683ef8) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ebfaaf0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e75f0f0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e75f0f0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e75f0f0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce51cd8) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce63408) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ebfaaf0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce82970) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6cda60) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6df190) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1cea8c08) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e73c290) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e7536d0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e747cb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e736580) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e730870) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e75f0f0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e72ab60) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce63408) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce51cd8) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6cda60) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce82970) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6e4ea0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1cea8c08) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e730870) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e7536d0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e73c290) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e747cb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e736580) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e683ef8) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e781f50) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6df190) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e72ab60) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e781f50) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6e4ea0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e683ef8) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ebfaaf0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e75f0f0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e75f0f0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e75f0f0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce51cd8) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce63408) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ebfaaf0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce82970) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6cda60) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6df190) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1cea8c08) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e73c290) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e7536d0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e747cb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e736580) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e730870) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e75f0f0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e72ab60) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce63408) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce51cd8) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6cda60) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce82970) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6e4ea0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1cea8c08) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e730870) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e7536d0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e73c290) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e747cb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e736580) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e683ef8) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e781f50) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6df190) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e72ab60) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e781f50) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6e4ea0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e683ef8) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ebfaaf0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e75f0f0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e75f0f0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e75f0f0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce51cd8) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce63408) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ebfaaf0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce82970) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6cda60) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6df190) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1cea8c08) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e73c290) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e7536d0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e747cb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e736580) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e730870) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e75f0f0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e72ab60) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce63408) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce51cd8) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6cda60) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce82970) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6e4ea0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1cea8c08) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e730870) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e7536d0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e73c290) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e747cb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e736580) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e683ef8) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e781f50) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6df190) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e72ab60) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e781f50) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6e4ea0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e683ef8) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ebfaaf0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e75f0f0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e75f0f0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e75f0f0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce51cd8) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce63408) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ebfaaf0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce82970) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6cda60) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6df190) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1cea8c08) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e73c290) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e7536d0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e747cb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e736580) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e730870) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e75f0f0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d_shader:shader_glsl_select >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glUseProgramObjectARB @ glsl_shader.c / 3226
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e72ab60) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce63408) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce51cd8) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6cda60) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ce82970) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6e4ea0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1cea8c08) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e730870) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e7536d0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e73c290) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e747cb0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e736580) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e683ef8) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e781f50) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6df190) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e72ab60) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e781f50) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e6e4ea0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1e683ef8) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x1ebfaaf0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:avifile:AVIFileExit (): stub!
Reference Count for Material __lookupviewpanel (1) != 0
Reference Count for Material vgui/zoom (1) != 0
```

Wine Configuration everything is at its default values

Hardware Specs :
AMD Athlon 64 Dual Core 4000+
2GB RAM
ATI HD 2600 Pro
i used envy to install the drivers for the video card

hope thats enough information......

---

### Post by aoanla on 2008-02-25
So, try adding -dxlevel 81 to the launch options for HL2 (under Properties on the My Games tab). That might help - it looks like your issue is DX9/shader related.

---

### Post by rebirthflame on 2008-02-25
ok that sorts out my graphical problems to some extent the start upi screen looks more like it should do however when i start the game the gmans face is now almost invisible and it still crashes after around 30 secs, this time it crashed i couldnt do anything about it whereas before i could force it to quit with alt+f4 no button combinations (that i know work) so i wasnt able to get a terminal output, any idea what this could be?

---

### Post by tetebueno on 2011-06-06
-dxlevel 81

... this fixed the eyes issue. Remember, if the main character is not Gordon Freeman, then it's not a game.

---

