---
title: "OpenGL not working in Wine"
date: 2007-10-19
forum: Wine
---

### Post by MrNatewood on 2007-10-19
This has only started to happen after i upgraded to gutsy gibbon today.
Before I upgraded I had no problem playing Call of Duty but now when I strart the game this error message pops up:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=46835&stc=1&d=1192806991[/IMG]

I am using nvidia-glx restricted drivers for my GeForce FX5600 ultra.
Wolfenstein: ET works fine(native linux version), so does glxgears.

I have tried running COD as sudo but that didn't help.
I also tried completely removing wine and re-installing and that didn't change anything either.

this is the console output:
```

Initializing OpenGL driver
...GLW_ChoosePFD( 32, 24, 8 )
...0 PFDs found
...hardware acceleration found
...PIXELFORMAT 1 selected
...creating GL context: succeeded
...making context current: succeeded
...WARNING: fullscreen unavailable in this mode
...shutting down QGL
...unloading OpenGL DLL
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Hunk_Clear: reset the hunk ok
Could not load OpenGL.  Make sure that you have the latest drivers for your video card from the manufacturer's web site.

```

Can anyone help in fixing wine's OpenGL support?

---

