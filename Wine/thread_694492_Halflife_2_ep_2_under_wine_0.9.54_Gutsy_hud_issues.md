---
title: "Halflife 2 ep 2 under wine 0.9.54 Gutsy hud issues"
date: 2008-02-12
forum: Wine
---

### Post by sticksabuser on 2008-02-12
Hey All,

So I got Wine 0.9.54 under Gutsy, a 8400M GS video card on a Dell Inspiron 1420 laptop with the latest 169.09 drivers from nvidia installed through envy. HL2 ep2 is loaded up through steam, which works pretty well in wine. The game seems to work fairly well also, however I get this weird issue:

[[IMG]http://img254.imageshack.us/img254/1567/screenshottl7.th.jpg[/IMG]](http://img254.imageshack.us/my.php?image=screenshottl7.jpg)

As you can see, everything is fine, I just can't see anything related to the HUD, except for black boxes (including the Pause box in the middle). Also note that I can't see the animated text on the intro screen, only black boxes in there place. Here's the output I get over and over again: 
```
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
fixme:d3d_texture:IWineD3DTextureImpl_PreLoad Texture (0x253e4220) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler
fixme:d3d_texture:IWineD3DTextureImpl_PreLoad Texture (0x253e4220) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler

```

Any help and suggestions is much appreciated. Also, a bit off topic, but does anyone know how to overclock the above video card... I tried coolbits and NVclock 0.8b3 to no avail...

Thanks...

---

### Post by Melhisedek on 2008-02-12
I have the same problem with Team Fortress 2. Try starting the game with -dxlevel 81 flag. It should work after that

---

### Post by sticksabuser on 2008-02-13
Thanks for the tip Melhisedek!... I can see everything now, plus I get a performance boost since the dx8.1 path is less intensive... 

Good stuff... Wine seems to get better with age! :p Pun intended....:lolflag:

---

