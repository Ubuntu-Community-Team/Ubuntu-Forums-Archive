---
title: "Starcraft &quot;cure for Slowness&quot; help"
date: 2008-06-02
forum: Wine
---

### Post by no1cares on 2008-06-02
So, when i go to play starcraft under wine, it is really slow.  i found this


> Cure for slowness

If the game runs slow on your machine then look at this page 
[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

Use the key "DirectDrawRenderer" and add that to your registry with the value "opengl"; you may also need to add the key "RenderTargetLockMode" with the value "readtex".

(Found under HKEY_CURRENT_USER/Software/Wine/Direct3D using regedit) 
taken from here [http://appdb.winehq.org/objectManager.php?sClass=version&iId=149](http://appdb.winehq.org/objectManager.php?sClass=version&iId=149)  (scroll down)

i dont have Direct3D in the location HKEY_CURRENT_USER/Software/Wine/Direct3D so i understand to create one...

the part i dont get is "Use the key "DirectDrawRenderer" and add that to your registry with the value "opengl"; you may also need to add the key "RenderTargetLockMode" with the value "readtex"."

can someone explain what that means.. also the stuff on the website link
[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys) (the one from the quote)

i am under the impression i need to add those registry's under the Direct3D but not sure.. PLease Help
thanks

---

### Post by Amerinidiot1231 on 2008-06-17
i also dont have the direct3d value

---

### Post by Amerinidiot1231 on 2008-06-17
look here

[http://backports.ubuntuforums.com/showthread.php?p=5095486](http://backports.ubuntuforums.com/showthread.php?p=5095486)

at the bottom it says you must create the value direct3d

It works for me

Helped the slowness some.

---

### Post by emwine on 2008-06-18
> **no1cares said:**
> i dont have Direct3D in the location HKEY_CURRENT_USER/Software/Wine/Direct3D so i understand to create one...

I do not recommend fussing with this value because it will affect all wine apps.  Instead set an appdefault for starcraft.  Save the following as a .reg file, say: scopengl.reg.
```
REGEDIT4

[HKEY_CURRENT_USER\Software\Wine\AppDefaults\StarCraft.exe\Direct3D]
"DirectDrawRenderer"="opengl"
"RenderTargetLockMode"="readtex"


```

Then issue:
```
wine regedit scopengl.reg
```

It's really too bad Starcraft still doesn't work properly in wine, as old and popular as it is.  It's been on the verge of working perfectly for years, but it seems it never will.

---

