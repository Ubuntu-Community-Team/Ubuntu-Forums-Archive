---
title: "Is my computer good enoguh"
date: 2008-05-17
forum: Wine
---

### Post by Elvish Legion on 2008-05-17
For wow?

Specs

AMD 2.4 processor (Not dual core)
1 gig ram
Nvidia 6200 

On windows I can avg anywhere from 25-35 fps,

On linux I seem to struggle to get 10fps,

I've tried the registry tweak, is there anything else I can do to help the fps?  The wine build is from the repos, forget which verison that is, same with nvidia drivers.

Thanks

---

### Post by aoanla on 2008-05-18
Which release of Ubuntu? 7.10 or 8.04?

In either case, the nVidia drivers in the default repos are a little old. Certainly, I've seen fps increases moving from the 7.10 default nVidia drivers to more recent releases (I forget how new the 8.04 drivers are, so the change may be less significant here).

The version of wine in the 8.04 repos is reasonably up to date, so I don't think you'd get significant performance increases from upgrading - the version of wine with 7.10 is *ancient*, and really should be upgraded from.

Other than that - have you tried running in OpenGL rather than DirectX mode?

---

### Post by TenPlus1 on 2008-05-18
Try going into the nvidia-settings in terminal and turn ON vsync for your 3d, this improves speeds for wine and them game itself while still giving you smooth 3d.

---

### Post by Elvish Legion on 2008-05-18
Well I just reinstalled debian testing, going to see if maybe some slightly updated software helps, 

Right now my cat/proc for nvidia driver reads

NVRM version: NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
GCC version:  gcc version 4.1.3 20080420 (prerelease) (Debian 4.1.2-22)
debian:/home/jduvall# 

So they are a couple months dated, but not so bad

jduvall@debian:~$ wine --version
wine-1.0-rc1

Wines also up to date,

Wish me luck, if it works better this time I'll have to update ubuntu to 8 and try it again

---

### Post by Elvish Legion on 2008-05-18
I seem even worse off than before, now starting the game without -opengl flag opens a lot of missing textures

With opengl flag I get an error

Your 3d accelerator card is not supported by World of Warcraft. Please install a 3d Accelerator card with dual-tmu support 

 glxinfo |grep render
direct rendering: Yes
OpenGL renderer string: GeForce 6200/AGP/SSE2
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 

Could it be, for some reason glxgears only puts out fps....which is uber low


Edit:

Updating to the driver from nvidia rids me of the error, seems the nvidia driver from feb = broken

---

### Post by igster on 2008-05-19
Not sure if you've seen it but the Ubuntu wiki entry is very helpful.

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

The article at WoWWiki is also very helpful - [http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)

OpenGL definitely works better.  The instructions in the wiki article explain how to edit your Config.wtf file to set that option.

Hope that helps!

---

