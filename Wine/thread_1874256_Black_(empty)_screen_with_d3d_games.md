---
title: "Black (empty) screen with d3d games"
date: 2011-11-02
forum: Wine
---

### Post by EliasYFGM on 2011-11-02
I am having this problem since I re-installed Linux Mint 10 (amd64) with all updates and Wine 1.2.3 with the d3dx9 libraries.

Running any game that depends of the Direct3D libraries just shows an empty black screen. Sounds can be heard but the rendering is just black, making the game unplayable.
This is the output log when running a game in the Terminal:

```
err:d3d:swapchain_blit >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Swapchain present blit(EXT_framebuffer_blit)
 @ swapchain.c / 136
err:d3d:swapchain_blit >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Swapchain present blit(EXT_framebuffer_blit)
 @ swapchain.c / 136
err:d3d:swapchain_blit >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Swapchain present blit(EXT_framebuffer_blit)
 @ swapchain.c / 136
err:d3d:swapchain_blit >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Swapchain present blit(EXT_framebuffer_blit)
 @ swapchain.c / 136
err:d3d:swapchain_blit >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from Swapchain present blit(EXT_framebuffer_blit)
 @ swapchain.c / 136
...
```

OpenGL games render normally, but Direct3D ones do not render anything on the screen.

My videocard is a GeForce GT 240. I've installed all the d3dx9 runtimes but did not work.

I've been searching through the web but all I could find are threads with no replies. Any suggestions?

---

