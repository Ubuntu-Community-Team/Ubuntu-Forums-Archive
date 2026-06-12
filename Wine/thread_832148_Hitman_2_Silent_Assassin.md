---
title: "Hitman 2 Silent Assassin"
date: 2008-06-17
forum: Wine
---

### Post by Grone1985 on 2008-06-17
Hi everyone,
I need help with this one please! Checked on Wine AppDB but I can't get it to work (I did the Hitman.ini thing), install worked fine but when I run the game I get this...

```
maitreyi@maitreyi-laptop:~/.wine/drive_c/Program Files/Eidos Interactive/Hitman 2 Silent Assassin$ wine hitman2.exe
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(800,600)
err:wgl:X11DRV_GetPixelFormat Unable to find a WineGLPixelFormat for iPixelFormat=0
err:wgl:X11DRV_wglCreateContext Cannot get FB Config for iPixelFormat 0, expect problems!
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 240, std (d/m/y): 30/03/2008, dlt (d/m/y): 12/10/2008
err:seh:setup_exception_record stack overflow 912 bytes in thread 0009 eip 7bc4f8fc esp 00230fa0 stack 0x230000-0x231000-0x330000

```

Any help? I'm running on Wine 0.9.59, Hardy 64x, ATI video card properly installed and working.

---

### Post by cogadh on 2008-06-17
Are you running Desktop Effects/Compiz? If so, disable them before you try running the game in Wine.

---

### Post by Grone1985 on 2008-06-17
> **cogadh said:**
> Are you running Desktop Effects/Compiz? If so, disable them before you try running the game in Wine.

No, I'm not, I'm trying Wine 1.0 to see if that fixes it. I'll post back

---

### Post by jmiguel77 on 2009-08-13
hi, i have other problem

i have an .iso image of hitman2

i mounted it in /media/iso/, ran the installer and everything went ok

but then, i make wine autorun.exe and hit play, it keep asking for the cd 

what can i do ???

---

### Post by NightMKoder on 2009-08-13
> **jmiguel77 said:**
> hi, i have other problem

i have an .iso image of hitman2

i mounted it in /media/iso/, ran the installer and everything went ok

but then, i make wine autorun.exe and hit play, it keep asking for the cd 

what can i do ???

Why are you expecting this to work? Isn't there some sort of copy protection on the game?

Also don't bring up year-old threads.

---

