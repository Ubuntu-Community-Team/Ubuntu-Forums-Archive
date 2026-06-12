---
title: "Deus Ex errors, &quot;err:module:attach_process_dlls &quot;Core.dll&quot; failed to initialize&quot;"
date: 2008-11-18
forum: Wine
---

### Post by Phil Urich on 2008-11-18
To be specific, it looks like this:

```
err:module:attach_process_dlls "Core.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\sda2\\games\\DeusEx\\System\\DeusEx.exe" failed, status c0000005
```

Funny thing is, this install is a copy paste from a copy-paste on my older computer which is also running Wine 1.1.8 (the original install was on a Win98 machine) . . . and works fine! The main difference between these two systems is that my primary computer is on 64-bit.  To break it down precisely:

Main computer: Wine 1.1.8, 64-bit, 4GB RAM, Hardy: won't run
2nd  computer: Wine 1.1.8, 32-bit, 1GB RAM, Intrepid: runs fine

The only support articles I could find were [this wine bug thread]("http://bugs.winehq.org/show_bug.cgi?id=1864") (whose solutions didn't at all work for me and, since on my old computer I'm using builtin dlls, it doesn't make sense that I would need to be using native Windows ones anyways) and then [this one in french]("http://www.playonlinux.com/forums/see_topic.php?topic=1627") in which, though I don't really know french, nothing seems to have been resolved.

I'm definitely willing to use my spare laptop as a test bed if anyone has any would-require-a-wacky-environment test ideas, even, I'm rather desperate to get this working.

---

### Post by Progressive on 2008-11-18
The easiest thing to do would be to look for Core.dll either on your Deus Ex CD or online somewhere like dll-files.com, and install it either to your Game Directory or your Windows System32 folder (in ~/.wine)

---

### Post by Phil Urich on 2008-11-23
Well . . . but there already IS a Core.dll there (in the folder for the game), and the exact same copy works absolutely fine on my i386 computer.

Furthermore, replacing the Core.dll file there (which I'm quite sure is an UnrealEngine-related file, not a generic Windows library) with the one from dll-files.com results in this:

```

err:module:import_dll Library zlib.dll (which is needed by L"Z:\\media\\sda2\\games\\DeusEx\\System\\Core.dll") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\media\\sda2\\games\\DeusEx\\System\\Core.dll") not found
err:module:import_dll Library Core.dll (which is needed by L"Z:\\media\\sda2\\games\\DeusEx\\System\\Window.dll") not found
err:module:import_dll Library Window.dll (which is needed by L"Z:\\media\\sda2\\games\\DeusEx\\System\\DeusEx.exe") not found
err:module:import_dll Library zlib.dll (which is needed by L"Z:\\media\\sda2\\games\\DeusEx\\System\\Core.dll") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\media\\sda2\\games\\DeusEx\\System\\Core.dll") not found
err:module:import_dll Library Core.dll (which is needed by L"Z:\\media\\sda2\\games\\DeusEx\\System\\DeusEx.exe") not found
err:module:import_dll Library zlib.dll (which is needed by L"Z:\\media\\sda2\\games\\DeusEx\\System\\Core.dll") not found
err:module:import_dll Library MFC42.DLL (which is needed by L"Z:\\media\\sda2\\games\\DeusEx\\System\\Core.dll") not found
err:module:import_dll Library Core.dll (which is needed by L"Z:\\media\\sda2\\games\\DeusEx\\System\\Engine.dll") not found
err:module:import_dll Library Engine.dll (which is needed by L"Z:\\media\\sda2\\games\\DeusEx\\System\\DeusEx.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\sda2\\games\\DeusEx\\System\\DeusEx.exe" failed, status c0000135

```

...oh hey, wait.  I just looked up other examples of "status c0000005" and it seems to be often a permissions problem, so I checked the drive's settings and indeed, the permissions are a bit wonky and thus aren't allowing exec.  I copied the folder to a drive that's ext3 and isn't noexec and it ran fine, with the exception that I seem to be stuck using DirectX as the renderer (it simply goes blank-screen if I choose OpenGL).  I'll probably try and see if either of the renderers at [http://cwdohnal.home.mindspring.com/utglr/](http://cwdohnal.home.mindspring.com/utglr/) work instead, although performance isn't exactly a problem since although it's a bit laggy on my older computer and its FX5600, with this 7800GTX it can take quite a bit of inefficiency ;) Next up, finding the right dlls to get UnrealEd working...

---

