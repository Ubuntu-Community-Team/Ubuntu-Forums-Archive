---
title: "Team Fortress 2, Steam and 3D Games Performance"
date: 2008-09-21
forum: Wine
---

### Post by linuxvacuum on 2008-09-21
Team Fortress 2 works but I get frequent stutters even when it has its on desktop and I renice hl2.exe to -3. The virtual desktop with wine is excellent, no more alt+tab fullscreen resolution changing madness.

The game puts an asterisk aside low texture quality in the video options of the gameeven if my card has 256 MB of memory. When I had the game installed in Windows the asterisk selected high texture quality.

So I am wondering how can wine properly detect my video card's RAM amount and what are the general configuration tips to enhance wine games performance?

---

### Post by linuxvacuum on 2008-09-21
I added this to my registry in ~/.wine/user.reg and it improved the performance! Thanks to different suggestions found on the web.

[Software\\Wine\\Direct3D]

"DirectDrawRender"="opengl"
"OffscreenRenderingMode"="fbo"
"PixelShaderMode"="enabled"
"UseGLSL"="enabled"
"VertexShaderMode"="hardware"
"VideoMemorySize"="256"

---

