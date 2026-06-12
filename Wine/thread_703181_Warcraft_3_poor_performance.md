---
title: "Warcraft 3 poor performance"
date: 2008-02-21
forum: Wine
---

### Post by HanDy_man on 2008-02-21
Quke 3 ,Unreal Tournament ,CS are running fine but Warcraft 3 lags alot (compared to Windowz Xp). I've try to run it with wine (9.55 9.48) and cedega with and w/o -OpenGL, I've try different drivers and kernels (2.6.22-14-generic 2.6.24.2 make oldconfig + P4 optimization), I've try to run in it's own X session, and still laging (even with super low resolution and details). When I'm in the menu, performance seems normal but when I choose map... horror.

my spec:

Celeron 1.72 Willamette
2x128 SDRAM 133MHZ
GF 2 MX400 64MB 200/333
500MB swap

and wine ouput:

> handy@desk:~$ wine '/media/sda1/Warcraft III/Frozen Throne.exe' -opengl
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x34f3d8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f64c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f67c,0x00000000), stub!
handy@desk:~$ fixme:imm:ImmGetOpenStatus (0x1340a0): semi-stub
fixme:imm:ImmReleaseContext (0x30028, 0x1340a0): stub
fixme:imm:ImmGetOpenStatus (0x1340a0): semi-stub
fixme:imm:ImmAssociateContextEx (0x30028, (nil), 16): stub
handy@desk:~$ 

After restart 97MB of memory is used (same for Windowz XP) and color is 16bits, restricted drivers are enabled.

Allmighty buck will solve my problem but that's not the point.

Ideas how to solve the problem?

---

### Post by kopilo on 2008-02-21
delete this post, posted on wrong thread.

---

