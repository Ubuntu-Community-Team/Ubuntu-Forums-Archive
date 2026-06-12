---
title: "setting directdrawrenderer to opengl?"
date: 2011-08-13
forum: Wine
---

### Post by Gamer456 on 2011-08-13
How exactly do I do this? I know to go to regedit then go to the Direct3D, then what do I do from there?

---

### Post by Brebs on 2011-08-13
This is the console method - run this exactly, including the dash at the end:
```
echo -e "[HKEY_CURRENT_USER\\Software\\Wine\\Direct3D]\n\"DirectDrawRenderer\"=\"opengl\"" | wine regedit -
```
Some miscellaneous others, while I'm at it:
```
echo -e "[HKEY_CURRENT_USER\\Software\\Wine\\Direct3D]\n\"DirectDrawRenderer\"=\"gdi\"" | wine regedit -

echo -e "[HKEY_CURRENT_USER\\Software\\Wine\\Direct3D]\n\"OffscreenRenderingMode\"=\"backbuffer\"" | wine regedit -
echo -e "[HKEY_CURRENT_USER\\Software\\Wine\\Direct3D]\n\"OffscreenRenderingMode\"=\"fbo\"" | wine regedit -
echo -e "[HKEY_CURRENT_USER\\Software\\Wine\\Direct3D]\n\"OffscreenRenderingMode\"=\"pbuffer\"" | wine regedit -

# enabled should be faster
echo -e "[HKEY_CURRENT_USER\\Software\\Wine\\Direct3D]\n\"Multisampling\"=\"enabled\"" | wine regedit -
echo -e "[HKEY_CURRENT_USER\\Software\\Wine\\Direct3D]\n\"Multisampling\"=\"disabled\"" | wine regedit -

# Don't bother with
echo -e "[HKEY_CURRENT_USER\\Software\\Wine\\Direct3D]\n\"RenderTargetLockMode\"=\"readdraw\"" | wine regedit -
echo -e "[HKEY_CURRENT_USER\\Software\\Wine\\Direct3D]\n\"RenderTargetLockMode\"=\"readtex\"" | wine regedit -

# This screws up dmix, so e.g. halflife2 crashes at startup!
echo -e "[HKEY_CURRENT_USER\\Software\\Wine\\Alsa Driver]\n\"UseDirectHW\"=\"y\"" | wine regedit -  # Maybe help buffer underruns

# Mouse warp
echo -e "[HKEY_CURRENT_USER\\Software\\Wine\\DirectInput]\n\"MouseWarpOverride\"=\"force\"" | wine regedit -

# Maybe useful sometimes
echo -e "[HKEY_CURRENT_USER\\Software\\Wine\\Direct3D]\n\"UseGLSL\"=\"disabled\"" | wine regedit -

# If keyboard is not responsive
echo -e "[HKEY_CURRENT_USER\\Software\\Wine\\X11 Driver]\n\"Managed\"=\"Y\"" | wine regedit -
echo -e "[HKEY_CURRENT_USER\\Software\\Wine\\\\Explorer]\n\"Desktop\"=\"Default\"" | wine regedit -
echo -e "[HKEY_CURRENT_USER\\Software\\Wine\\\\Explorer\\\\Desktops]\n\"Default\"=\"1920x1080\"" | wine regedit -

# DLL overrides
echo -e "[HKEY_CURRENT_USER\\Software\\Wine\\DllOverrides]\n\"winegstreamer\"=\"\"" | wine regedit -
```

---

