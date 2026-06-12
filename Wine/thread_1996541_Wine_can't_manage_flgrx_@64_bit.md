---
title: "Wine can't manage flgrx @64 bit"
date: 2012-06-04
forum: Wine
---

### Post by editheraven on 2012-06-04
I have Ubuntu natty (i kinow, it's old, i love it) x86_64, original ati driver from ati/amd site x86_64 version. Any solid 3d app/game runs fine pn ubuntu. I have good 3d acceleration. When it comes to wine it can't do a thing. For example, when i run warcraft3

```
err:ole:CoCreateInstance apartment not initialised
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
fixme:advapi:SetSecurityInfo stub
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D8 is not available without OpenGL.
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D8 is not available without OpenGL.
fixme:msvcr90:__clean_type_info_names_internal (0x150591a0) stub

```

What can i do?

---

### Post by dino99 on 2012-06-04
seems you need to install dxd9 with winetricks

have you installed wine 1.5.5 ?

---

### Post by drs305 on 2012-06-04
Thread moved to Wine subforum.

---

### Post by editheraven on 2012-06-04
I have all dx libraries installed. I have "wine-1.4"installed from its official repos.

---

### Post by thatguruguy on 2012-06-04
If you love 11.04, you'll REALLY love 12.04.

I'm guessing this is a driver issue, and you'd have better luck with 12.04.

---

### Post by editheraven on 2012-06-05
then why legacy apps that runs dirrectly on opengl works flawless? My guessing is that is a problem with wine integrating with the driver.

---

### Post by editheraven on 2012-06-06
Anyone with 12.04@64 bit confirming that packaged wine is working without manual compiling?

---

