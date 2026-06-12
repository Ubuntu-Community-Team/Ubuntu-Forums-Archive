---
title: "FIFA 07 and Wine problem"
date: 2008-11-13
forum: Wine
---

### Post by firedevilbg on 2008-11-13
Hi all...
I installed FIFA 07 with Wine and when i started the game it seems working nice... but when I started to play a soccer match I can't see the ball...
There was only the shadow of the ball...
Please help!

---

### Post by cogadh on 2008-11-13
FIFA 07 has a spotty history with Wine (at best), this could be just how it works:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=4277](http://appdb.winehq.org/objectManager.php?sClass=application&iId=4277)

However, it may help to know some info about your system, such as Ubuntu version, Wine version, hardware specs and any terminal output from Wine.

---

### Post by firedevilbg on 2008-11-16
> **cogadh said:**
> FIFA 07 has a spotty history with Wine (at best), this could be just how it works:
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=4277](http://appdb.winehq.org/objectManager.php?sClass=application&iId=4277)

However, it may help to know some info about your system, such as Ubuntu version, Wine version, hardware specs and any terminal output from Wine.


Ubuntu version  is 8.10
Wine version is 1.0.1
Hardware: 
Motherboard ECS KT600-A SATA/LAN/Sound
CPU AMD XP Barton 2500+ 1.2GHz(333)
RAM DDR 1GB 400MHz
Video card ATI Radeon 9200SE 128MB DDR 

Terminal output from Wine
```
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13b098) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13b098) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13b098) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13b098) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13b098) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13b098) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13b098) : stub
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexParameteri GL_TEXTURE_MAX_ANISOTROPY_EXT ... @ basetexture.c / 492
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from glTexParameteri GL_TEXTURE_MAX_ANISOTROPY_EXT ... @ basetexture.c / 492
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13b098) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13b098) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13b098) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13b098) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x13b098) : stub

```
And wine repeats this again and again...

---

### Post by cogadh on 2008-11-16
Well, the "fixme" messages are not really errors as much as notes from the Wine developers about incomplete or unimplemented functions in Wine, so you can't really fix them. 

However, that one "fixme" message references an invalid value and anisotropic filtering. Have you tried simply turning off anisotropy in the game's options to see if that changes anything?

---

### Post by firedevilbg on 2008-11-18
I just set lower resolution and it works just fine! :guitar:

---

