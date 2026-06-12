---
title: "Team Fortress 2 fps"
date: 2008-05-21
forum: Wine
---

### Post by p3ng0 on 2008-05-21
TF 2 runs decent half the time (40-60 fps) but the other half it runs around 10 fps and has the following errors over and over the entire time while playing:

> fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_PERFORMANCE_INFORMATION
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
fixme:d3d:handleStreams Tweening is only valid with vertex shaders
fixme:d3d:handleStreams Tweening is only valid with vertex shaders
fixme:d3d:handleStreams Tweening is only valid with vertex shaders
fixme:d3d:handleStreams Tweening is only valid with vertex shaders
fixme:d3d:handleStreams Tweening is only valid with vertex shaders
fixme:d3d:handleStreams Tweening is only valid with vertex shaders
fixme:d3d:handleStreams Tweening is only valid with vertex shaders
fixme:d3d:handleStreams Tweening is only valid with vertex shaders
fixme:d3d:handleStreams Tweening is only valid with vertex shaders
fixme:d3d_draw:depth_copy Not supported with fixed up depth stencil
fixme:d3d_draw:depth_copy Not supported with fixed up depth stencil


---

### Post by ChiaGod on 2008-05-21
I'm experiencing the same output:

```
fixme:d3d:handleStreams Tweening is only valid with vertex shaders

fixme:d3d_draw:depth_copy Not supported with fixed up depth stencil
```

Running Half-Life 2: Episode 2 with directX set to 8.1.  The game slows down, stutters, and eventually freezes at this point.

HW: 
Geforce 8600 GTS x2
AMD Athlon 64 x2

I am using the following launch options (set within steam - game properties) w/ HL2.exe which did reduce stuttering:
```

 -novid -dxlevel 81  -width 3840 height 1024 -console -heapsize 512000

```
The heapsize argument is what I added to reduce the stuttering.


I am launching steam with the following:


```
env WINEPREFIX="/home/sysop/.wine" wine explorer /desktop=SteamTriple,3840x1024 "C:\Program Files\Steam\Steam.exe"

```

I've tried setting dxlevel to 70 80 81 90 with similar results (game speed varies, but the stuttering and the error messages above seem unavoidable).

---

