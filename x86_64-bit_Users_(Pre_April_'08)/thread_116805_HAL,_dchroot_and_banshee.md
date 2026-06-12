---
title: "HAL, dchroot and banshee"
date: 2006-01-13
forum: x86 64-bit Users (Pre April '08)
---

### Post by jmcelroy on 2006-01-13
I'm getting the following error when trying to start banshee from inside dchroot,  any suggestions ?  I've tried to install/start dbus and hal from inside the chroot but hal refuses to start.


0: Active Player Engine is now 'GStreamer'
1: Loaded PlayerEngine core: GStreamer
2: Loaded AudioCdPlayerEngine core: GStreamer

Unhandled Exception: System.ApplicationException: Could not initialize HAL for CD Detection
in [0x000c0] Banshee.AudioCdCore:.ctor ()
in [0x00170] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/Core.cs:174) Banshee.Core:.ctor ()
in [0x0000b] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/Core.cs:73) Banshee.Core:get_Instance ()
in [0x000ef] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/Main.cs:78) Banshee.BansheeEntry:Main (System.String[] args)
(

---

