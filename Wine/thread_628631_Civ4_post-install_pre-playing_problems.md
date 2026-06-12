---
title: "Civ4 post-install pre-playing problems"
date: 2007-12-01
forum: Wine
---

### Post by sayhar on 2007-12-01
Hi. After about a week of tinkering, I've finally managed to (sort of ) install Civ 4.

There are some things that should show up (say the how-tos) but don't.

For example, under regedit, I have no "Direct3D" folder under HKEY_CURRENT_USER->Software->Wine

If that's not there, I can't change my videomemorysize.

Civ4 does bring up popus telling me my videomemory size is too low, but if I understand correctly, that's because the default is set to 64mb, while i have a 128mb card.



My problem stems from this, I think.
```
err:menubuilder:WinMain failed to build menu item for C:\Program Files\Civ4\CivilizationIV.ini.lnk

```


Full output of terminal: (minus fixme:'s)

```

me@mycomputer: wine Civilization4.exe 
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:menubuilder:WinMain failed to build menu item for C:\Program Files\Civ4\Saves.lnk
err:menubuilder:WinMain failed to build menu item for C:\Program Files\Civ4\Logs.lnk
err:menubuilder:WinMain failed to build menu item for C:\Program Files\Civ4\CivilizationIV.ini.lnk
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:d3d:getColorBits Unsupported format: WINED3DFMT_A32B32G32R32F
err:d3d:IWineD3DImpl_IsPixelFormatCompatibleWithRenderFmt Unable to check compatibility for Format=WINED3DFMT_A32B32G32R32F
err:xrandr:X11DRV_XRandR_SetCurrentMode Resolution change not successful -- perhaps display has changed?
fixme:system:SystemParametersInfoW Unimplemented action: 55 (SPI_SETMOUSEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!
err:d3d_surface:surface_prepare_system_memory Surface without memory or pbo has SFLAG_INSYSMEM set!


```

How do I fix, please?

---

### Post by happyhamster on 2007-12-01
You can make a text file containing:

[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"VideoMemorySize"="128"


Save it as: "desired-name-of-file.reg". You can import the file into the registry using:

wine regedit desired-name-of-file.reg

or just:

wine regedit

and choose to import it manually.

---

### Post by sayhar on 2007-12-01
Thanks! That's handy.

Now how can I let wine "build menu item for C:\Program Files\Civ4\CivilizationIV.ini.lnk" ,

please?


I need to have that file created so I can edit it and have sound work.

---

### Post by PaeTar on 2008-05-01
I also get pretty much all the same errors. Ive installed all the extra files in the /system32 folder. Game loads, but after the intro screen, wine just goes blue and crashes back to gnome.

---

### Post by bilal.17 on 2008-05-01
I installed Civ4 with the guide from this page, and now it works perfectly, except for some minor sound problems [http://appdb.winehq.org/objectManager.php?sClass=version&iId=5254]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=5254")

---

### Post by Raistlin82 on 2008-06-07
Hi all, a newbie here, am trying to play Civ 4 on my laptop running hardy, i've installed it with wine, installed the 1.74 patch and no cd patch.  when i attempt to run the game i get the following in an OK box

error locating tag node in setglobalclassinfo function
current xml file is: game info/civ4playeroptioninfos.xml

directly followed by another OK box which states

error locating tag node in setglobalclass info function
current xml file is: gameinfo/civ4graphicoptioninfos.xml

Its probably a really stupid question with an easy answer but any help would be much appreciated!!

---

### Post by NeoFax on 2008-06-08
Raistlin82:  Have you set msxml3.dll, msxml3r.dll and d3dx_36.dll as native in winecfg for Civilization4.exe?  If not, go to the Wine AppDB website and follow the directions there.  The game plays great under Hardy and the newest wine.

---

### Post by Raistlin82 on 2008-06-08
Pretty sure I have done that but will check it out, thanks for the reply!  Am having Civ withdrawel!!!

yeah tried it again, same problem unfortunately :( Think the best option would be just to try uninstalling and starting from scratch

---

### Post by Raistlin82 on 2008-06-10
I've uninstalled and tried to install civ 4 complete, installation runs fine, but get the same error as before, 2 xml errors, please help i need my civ fix! :(

Edit - Reinstalled with Civ complete, managed to install fine, and to get origional civ 4 to load, but it tells me that my system is below spec and may not run, when you actually try to play it hangs the whole system :(  Will just have to boot up windows me thinks, not done that in weeks :( but I miss it and it runs as designed there.

---

