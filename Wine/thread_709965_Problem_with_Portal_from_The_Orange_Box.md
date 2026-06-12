---
title: "Problem with Portal from The Orange Box"
date: 2008-02-27
forum: Wine
---

### Post by person_99 on 2008-02-27
I installed Portal from The Orange Box with a clean install of Wine 0.9.54. 
Things installed and updated much faster then in my Windows.

I just tried Portal, it looks better then windows (I actually get R, G, and B, not just R and G like in Windows), runs faster, but it isn't fullscreen, but has no window borders.

I am using a Geforce 6200 256mb ddr2, 
I am currently running with Compiz Fusion also running.

How can I get Portal to actually run in fullscreen?

Note: My desktop is currently at at least 1280 x 1024, or whatever insane resolution the Nvidia drivers defaulted at.
Note: Portal's settings are set to fullscreen mode.

---

### Post by person_99 on 2008-02-28
I tested Half Life 2 also, it gets very strange colors on the Valve logo and freezes on the license.



Edit: Ok, I found out that it was running with some D3d hal thing, and it just so happens that I have on an old harddrive Windows 2000 Professional with the latest DirectX 9.0c.

How can I get that version of DirectX from Windows into Wine?

---

### Post by Alpha7 on 2008-02-28
Download your normal Windows DirectX 9c installer, Follow this guide  [http://wine-review.blogspot.com/2007/11/directx-90c-on-linux-with-wine.html](http://wine-review.blogspot.com/2007/11/directx-90c-on-linux-with-wine.html)

---

### Post by ahaslam on 2008-02-28
> **Alpha7 said:**
> Download your normal Windows DirectX 9c installer, Follow this guide  [http://wine-review.blogspot.com/2007/11/directx-90c-on-linux-with-wine.html](http://wine-review.blogspot.com/2007/11/directx-90c-on-linux-with-wine.html)

**DO NOT DO THIS! **It will not solve your problem & will only cause further complications.

---

### Post by Alpha7 on 2008-02-28
and why is that?

---

### Post by Roryking on 2008-02-28
WINE must use it's own directx subsystem. Installing DX from Microsoft will only replace Wine's stuff with stuff that Wine cannot use. Wine developers are working on getting good DX9 support, but, it'll be awhile :-)

In the meantime, try this:

1. Disable Compiz. Unfortunately Compiz and Wine do not work together too well, especially in the context of a 3D-accelerated application like Portal (or any Source-engine game).
2. Open up Wine's registry editor:
```
wine regedit
```
and put these strings in HKEY_CURRENT_USER\Software\Wine\Direct3D:

```
OffscreenRenderingMode fbo
PixelShaderMode enabled
UseGLSL enabled
VideoMemorySize (size in megabytes, same as your onboard video memory i.e. 256)
```
Please note on that last one, you'll just put 256 (and not 256M as common sense would dictate :confused:)
3. Open up your wine configuration panel:
```
winecfg
```
and go to the Graphics tab, and make sure hardware acceleration is enabled.
4. Fire up Steam, and set these launch options for portal (click once on Portal from your games menu, and then click the "Properties" button, then "Set launch options..."
```
-dxlevel 81 -fullscreen -width 1280 -height 1024
```
or whatever resolution you feel is appropriate.

---

### Post by person_99 on 2008-03-01
Some of my friends told me to just rip the d3d9.dll from my Windows, will this work?

---

### Post by ahaslam on 2008-03-02
Only if it complains of missing .dll files. Though that should be a thing of the past with the release of Wine 0.9.56. 

It sounds more like a simple configuration problem though. For example, even though Portal is set to fullscreen, is the specified resolution the same as that of your desktop? I only mention this as you seem unsure of your resolution & it really could be as simple as that.

---

