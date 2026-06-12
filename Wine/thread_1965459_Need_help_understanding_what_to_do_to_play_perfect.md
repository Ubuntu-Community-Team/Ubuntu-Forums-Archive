---
title: "Need help understanding what to do to play perfect world international"
date: 2012-04-25
forum: Wine
---

### Post by Radical_Dreamer on 2012-04-25
So... I read it on wineHQ that:
"
Wine configuration: 

Windows -> "Windows XP" 
Allow Pixel Shader "enable" 
Audio only ALSA

Regedit configuration:

Add "Direct3D" key to HKEY_CURRENT_USR -> Software -> Wine 
Add the following String Values to the Direct3D key:


DirectDrawRenderer                          "opengl" 
Nonpower2Mode                                "repack" 
OffscreenRenderingMode                   "fbo" 
PixelShaderMode                                "enabled" 
RenderTargetLockMode                     "auto" 
UseGLSL                                             "disabled" 
VideoMemorySize                               "512"            < Edit this line to indicate the size of your video memory 

After that: 
Run winetricks with: 

sh ~/.wine/winetricks
 

You will have to install VCRUN6 via Winetricks. (date added: 4/7/2011) 
"

I can't really get anywhere after checking that windows is set to xp.  I don't know where allow pixel shader is and I checked the graphics part of wine and the audio is also confusing because I don't see anything concerning ALSA under the audio tab. Just the following:
HDA Intel-HDMI 0
HDA Intel-ALC663
so I'm not really sure.

The stuff after that I have little idea with so please help me :D

---

### Post by oldos2er on 2012-04-25
Moved to Wine.

---

### Post by cogadh on 2012-04-25
The first part is all done in winecfg, but other than the Windows version, the rest of those settings don't exist anymore (they are already the default settings), or at least not as they were described a year ago when that how-to was written (things can change fast in Wine).

The second part refers to editing the Wine registry, which you can do by running "wine regedit" in a terminal. Editing the Wine registry via this method is exactly the same as editing the Windows registry.

The winetricks thing is pretty straitforward: run "winetricks" in a terminal (the whole "sh ~/.wine/winetricks" command is no longer necessary, just typing "winetricks" will work fine), select the default prefix, then "Install a Windows DLL or component", then find vcrun6 on the list and click OK.

---

