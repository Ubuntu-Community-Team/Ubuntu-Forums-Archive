---
title: "WoW Freezing problem - may have found the problem"
date: 2007-12-08
forum: Wine
---

### Post by OisinT on 2007-12-08
Alright, so I know loads of people seem to be having the same problem with WoW freezing after the loading screen.  For me the bar hits 100% and it's finished after that.
I see all these fixes for ATI cards, but I'm (and some others are also) running Nvidia.... so this fix does nothing for us.

when I try to run:
```
wine WoW.exe
wine WoW.exe -d3d -opengl
wine WoW.exe -d3d
```
or anything that makes the d3d load, the freeze happens and I get this error

```
 @ query.c / 198
fixme:d3d:IWineD3DQueryImpl_GetData >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glGetQueryObjectuivARB(GL_QUERY_RESULT_AVAILABLE)
 @ query.c / 198
fixme:d3d:IWineD3DQueryImpl_GetData >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glGetQueryObjectuivARB(GL_QUERY_RESULT_AVAILABLE)
 @ query.c / 198
fixme:d3d:IWineD3DQueryImpl_GetData >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glGetQueryObjectuivARB(GL_QUERY_RESULT_AVAILABLE)
 @ query.c / 198
fixme:d3d:IWineD3DQueryImpl_GetData >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glGetQueryObjectuivARB(GL_QUERY_RESULT_AVAILABLE)
 @ query.c / 198
fixme:d3d:IWineD3DQueryImpl_GetData >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glGetQueryObjectuivARB(GL_QUERY_RESULT_AVAILABLE)
 @ query.c / 198
fixme:d3d:IWineD3DQueryImpl_GetData >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glGetQueryObjectuivARB(GL_QUERY_RESULT_AVAILABLE)
 @ query.c / 198
fixme:d3d:IWineD3DQueryImpl_GetData >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) from glGetQueryObjectuivARB(GL_QUERY_RESULT_AVAILABLE)
 @ query.c / 198
fixme:d3d:IWineD3DQueryImpl_GetData >>>>>>>>>>>>>>>>> GL_INVALID_OPERATION (0x502) Killed
oisint@OisinT1:~/.wine/drive_c/World of Warcraft$ 

```

but if i use

```
wine WoW.exe -opengl
```

the game will load, but the graphics and framerate are awful.


The way I was able to fix this was by adding these lines to the wtf/config.wtf file

```
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"

```

now my only problem is that it has gotten rid of my sound now.... lol

---

### Post by Ifrgtmyname on 2007-12-13
i have the same problem thanks for help =)

---

### Post by slade208 on 2007-12-20
Confirmed Fix 

Setup: Nvidia, Ubuntu 7.04

Thank you

-Steve

---

### Post by tombug on 2007-12-23
there is a registry config  you can do it should double your frame rate

[https://help.ubuntu.com/community/WorldofWarcraft#head-4b2ddfc20b64caffa3c5fbfad67a0480440ccad2](https://help.ubuntu.com/community/WorldofWarcraft#head-4b2ddfc20b64caffa3c5fbfad67a0480440ccad2)

---

