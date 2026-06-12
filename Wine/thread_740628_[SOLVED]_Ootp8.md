---
title: "[SOLVED] Ootp8"
date: 2008-03-30
forum: Wine
---

### Post by eriqjaffe on 2008-03-30
I'm running Xubuntu 8.04 (it's a WUBI install, if that makes a difference) with the nVidia restricted drivers, and I'm getting some bad graphical glitching when I try to play Out of the Park Baseball:

[img]http://img182.imageshack.us/img182/6294/ootpwinens0.jpg[/img]

Essentially, when I mouse over things, they start jumping around and becoming pretty much unreadable.  There's nothing graphically fancy going on in the game - certainly nothing fancy at the splash screen.  When I run from the terminal, it doesn't spit anything out, errors or otherwise.  If anybody has any ideas what to look into, I'd appreciate it.

---

### Post by happyhamster on 2008-03-31
- You could try testing different registry settings. Open a text editor and create an empty text file. Copy&paste:

[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"DirectDrawRenderer"="opengl"
"VideoMemorySize"="256"
"UseGLSL"="enabled"
"OffscreenRenderingMode"="fbo"
"RenderTargetLockMode"="auto"

- Save it as: "test1.reg" (make sure the VideoMemorySize is correct). Import it into the wine registry, using:

regedit test1.reg

- Now run the game to see if things have changed. If not, try different settings. (It's now easier to just run regedit and change things manually). Possible settings:

```

+-Direct3D
      |  |
      |  +->DirectDrawRenderer
      |  |   [Select what backend to use for DDraw. Valid options are:
      |  |    gdi - Use GDI to draw on the screen (slow but reliable) (default)
      |  |    opengl - Use OpenGL (fast but not all programs work correctly)
      |  |    see http://wiki.winehq.org/DirectDraw for more information]
      |  |
      |  +->RenderTargetLockMode
      |  |   [Selects which mode is used to read and write the framebuffer while it is locked.
      |  |    auto:     same as readdraw at the moment, will do benchmarks and use best method later(default)
      |  |    disabled: effectively disables render target locking
      |  |    readdraw: uses glReadPixels for reading, glDrawPixels for drawing
      |  |    readtex:  reading with glReadPixels, drawing by drawing a textured quad
      |  |    texdraw:  readback using a texture, drawing with glDrawPixels
      |  |    textex:   readback using a texture, drawing with a textured quad
      |  |    see http://wiki.winehq.org/DirectDraw for more information]
      |  |
      |  +->OffscreenRenderingMode
      |  |   [Selects which mode is used to render offscreen images/textures.
      |  |    backbuffer: the rendering is done in the backbuffer (default)
      |  |    pbuffer:    uses PixelBuffers
      |  |    fbo:        uses Framebuffer object]
      |  |
      |  +->UseGLSL
      |  |   [When set to "disabled", this disables the use of GL Shading Language for vertex
      |  |    and pixel shaders, it will result in a fallback to ARB shaders. By default GLSL 
      |  |    is enabled when available. (It is default as of 29/10/2007 or Wine 0.9.49)
      |  |
      |  +->VideoMemorySize
      |      [Sets the amount of emulated video memory. Default is a simple autodetection
      |       based on the card type guessed from OpenGL strings and extensions]
```

- First thing I would look at is the OffscreenRenderingMode. For more info, see:
[http://www.winehq.org/site/docs/wineusr-guide/using-regedit](http://www.winehq.org/site/docs/wineusr-guide/using-regedit)

---

### Post by eriqjaffe on 2008-04-01
Thanks, I'll give that a shot.

---

### Post by eriqjaffe on 2008-04-10
Turns out it was a driver issue.  Rolling back to to the 96.43.05 drivers with EnvyNG seems to do the trick.  Allegedly, there's a problem with the game's built-in FTP (which makes online leagues a bit tricky), but that can be dealt with.

[[IMG]http://img502.imageshack.us/img502/3299/scrot20080410225046nv4.th.png[/IMG]](http://img502.imageshack.us/my.php?image=scrot20080410225046nv4.png)

---

### Post by eriqjaffe on 2008-06-19
FWIW, OOTP9 was just released yesterday, and also seems to work just fine in Wine.

[[IMG]http://img205.imageshack.us/img205/782/scrot20080618231530oq5.th.jpg[/IMG]](http://img205.imageshack.us/my.php?image=scrot20080618231530oq5.jpg)

---

