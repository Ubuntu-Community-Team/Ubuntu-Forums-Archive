---
title: "Steam does not detect pixel shader"
date: 2008-05-05
forum: Wine
---

### Post by manaleak34 on 2008-05-05
After downloading Steam and Team fortress 2 with no issues I find myself unable to run it.

What occurs is that it goes through the into video and hits the loading screen for a few seconds and crashes.

A pop-up appears saying that my hardware does not support Pixel Shader 1.1.

The thing is I'm using a Radeon 9200 graphics card which has DirectX 8.1 and Pixel Shader 1.4. Also I've run the same game in Windows with no issues. I've already have tried the "-dxlevel 81" in the starting settings setup.

I'm assuming this may have something to do with Wine having DirectX 9 as the standard or me not having the right ATI drivers or something.

Any suggestions?

---

### Post by spoons on 2008-05-05
I think for pixel shaders you need an OpenGL 2 compatible card, and you only have an OpenGL 1.x compatible card. (just a wild stab in the dark)

---

### Post by Melcar on 2008-05-05
Wine uses opengl2.0 for many of its DX calls, so even if a game only needs DX8 to work in Windows, in Wine you will need full opengl2.0 support.

---

### Post by manaleak34 on 2008-05-05
So to work in Linux I need a new video card then?

Lovely... #-o

---

### Post by dmn_clown on 2008-05-05
[QUOTE=manaleak34]A pop-up appears saying that my hardware does not support Pixel Shader 1.1[/QUOTE]

Have you configured wine to use pixel shaders?  The check box is under the graphics tab in the winecfg ui.

[quote=Melcar]in Wine you will need full opengl2.0 support.[/quote]

Are you sure about that?

---

### Post by Melcar on 2008-05-05
> **dmn_clown said:**
> Have you configured wine to use pixel shaders?  The check box is under the graphics tab in the winecfg ui.



Are you sure about that?

That's what I heard from several Wine discussions.  It's the reason you can't use open source drivers (only opengl1.3 support) and ATI cards have very poor performance with some Wine games (not as good opengl2.0 support as nvidia cards).  Wine (the most recent versions anyway) enable pixel shader support by default, so chances are that if it doesn't work, it doesn't work.  Some of the registry tweaks might help thought:

[http://wiki.winehq.org/UsefulRegistryKeys]("http://wiki.winehq.org/UsefulRegistryKeys")

> **manaleak34 said:**
> So to work in Linux I need a new video card then?

Lovely... #-o

No.  To use Wine for games you may need another card.  Don't blame it on Linux.

---

### Post by roderick on 2008-05-05
You may want to check out the appdb entry for your game to see if anyone else has reported settings that work or do not work properly.

---

