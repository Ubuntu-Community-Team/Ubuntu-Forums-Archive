---
title: "Zsnes on 32bit chroot"
date: 2005-11-10
forum: x86 64-bit Users (Pre April '08)
---

### Post by yohan on 2005-11-10
I installled zsnes on a chroot and tried running it but I have a problem. When selecting anything except 640*480 software mode it really really lags. glfgears give me great fps and this is my fglrxinfo:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

Is this a common problem on 64 bit ubuntu? Ive heard that people have been having this problem with Zsnes but ive couldnt find a fix for it.

thanks!

---

### Post by BoyOfDestiny on 2005-11-21
[QUOTE=yohan]I installled zsnes on a chroot and tried running it but I have a problem. When selecting anything except 640*480 software mode it really really lags. glfgears give me great fps and this is my fglrxinfo:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

Is this a common problem on 64 bit ubuntu? Ive heard that people have been having this problem with Zsnes but ive couldnt find a fix for it.

thanks![/QUOTE]

Mine is working great, on a radeon 9250 (so my drivers are the open source ones)... On some other post someone suggested that you have the same driver etc in the chroot. So fire up synaptic32 and see if that helps... Best of luck!

EDIT: Or do you just mean slow with opengl accel... I think that might be an ATi issue...

---

### Post by kauffman77 on 2005-12-17
Found your post via a web search: I am experiencing a similar problem but on a debian system (please excuse the corss-distro post) with an Nvidia FX 5200 card. Running the regular open GL application (glxgears) works great but zsnes can't seem to make use of the GL library right. When I switch from the non-gl modes, which work well but have low resolution, to the GL mode, everything grinds to a hault or runs very slow. Let me know if you find any resolution to this.

One additional note: I've tried compiling zsnes from scratch with both the Mesa and proprietary Nvidia GL libraries to fix this problem with no success.

---

