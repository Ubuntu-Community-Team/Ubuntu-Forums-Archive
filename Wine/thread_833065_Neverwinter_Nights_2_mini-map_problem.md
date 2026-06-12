---
title: "Neverwinter Nights 2 mini-map problem"
date: 2008-06-18
forum: Wine
---

### Post by harvodan on 2008-06-18
Hello all.

I've successfully installed nwn2 plus mask of the betrayer, and everything's going well enough except for the mini-map in game being plain black. This is under wine 0.9.60, and with all appropriate registry settings set up, as well as dll overrides for devenum and dxdiagn. My nwn2.ini file looks like this:


Should I make any changes here? Should I be using a different version of wine? Can anyone report anything? Also, after disabling OffscreenRenderingMode=fbo, the minimap shows up correctly, but nothing else does. Please help.

[Sound Options]

Duck Time=0.500000

Duck Scale SFX=0.500000

Duck Scale Music=0.500000

Duck Audio In Cutscenes=1

Music Volume=0.85

Voice Volume=0.85

SoundFX Volume=0.85

Environment Effects=0

2D3D Bias=1.00

3D Provider=Miles Fast 2D Positional Audio

Number 2D Voices=16

Number 3D Voices=16



[Display Options]

FullScreen=1

Width=1024

Height=768

RefreshRate=-1

Gamma=1.012000



[Graphics Options]

Bloom=1

EnableVsync=0

Shadows=0

EnvironmentShadows=1

CharacterDropShadows=0

SoftShadows=0

FarShadows=0

PointLightShadows=0

UseHardwareShadowMapsIfAvailable=1

NormalMappedTerrain=1

NumberOfTextureMipLevelsToSkip=0

UseHDRIfAvailable=0

MultiSampleType=0

ScreenshotFormat=jpg

WaterReflections=0

WaterRefraction=0

RenderGrass=1

HiRezShadowMapSize=1024

LowRezShadowMapSize=1024

CharacterAndPointLightShadowMapSize=512

TextureMinFilterMode=3

TextureMagFilterMode=2

TextureMipFilterMode=2

TextureMaxAnisoTropy=1

FarClipPlaneModifier=1.000000

ATIWorkAroundForPointLightShadows=0

SoftwareSkinning=0

FirstRunAutoDetect=0

LightsPerObject=1000

SEFCacheTimeout=500

SEFCacheSize=20

---

### Post by harvodan on 2008-06-18
Anybody out there?

---

### Post by something random on 2009-07-10
I am getting the same problem and i'm not using linux or wine.

---

### Post by harvodan on 2010-01-06
For whomever might read this thread, simply turn anti aliasing off. There's some sort of problem with that and the nwn2 minimap.

---

