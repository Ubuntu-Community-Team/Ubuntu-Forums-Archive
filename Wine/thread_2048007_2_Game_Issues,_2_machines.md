---
title: "2 Game Issues, 2 machines"
date: 2012-08-25
forum: Wine
---

### Post by sdgiffin on 2012-08-25
On my daughter's laptop, I'm having a problem running AngryBirds under Wine 1.4: As soon as I choose a level to play, it crashes:
```
zoya@zoyas-laptop:~/.wine/drive_c/Program Files/Angry_Birds$ wine AngryBirds.exe
fixme:heap:HeapSetInformation 0x541000 0 0x32fd58 4
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
drmRadeonCmdBuffer: -12. Kernel failed to parse or rejected command stream. See dmesg for more info.
zoya@zoyas-laptop:~/.wine/drive_c/Program Files/Angry_Birds$
```So I checked dmesg, and here's what I get, though I can't tell for sure, I assume WINE is having an issue with the ATI card in the laptop for some reason:
```
[   69.059454] init: gdm main process (1096) killed by TERM signal
[   76.554494] init: plymouth-stop pre-start process (1298) terminated with status 1
[ 2059.364905] [drm:radeon_cs_ioctl] *ERROR* Failed to parse relocation -12!
[ 2651.520555] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[ 3477.801816] [drm:radeon_cs_ioctl] *ERROR* Failed to parse relocation -12!
[25091.460999] [drm:radeon_cs_ioctl] *ERROR* Failed to parse relocation -12!

```The other issue is with Jedi Outcast under WINE 1.5 on my laptop. I can play single player fine, but when I play multiplayer, my client cannot see local or Internet-based servers, and when I'm the server, no local clients can see me. As far as I know, there are no error logs being generated for this particular issue, but if anybody can help with either of these problems, I would be most appreciative!

On both laptops, I'm running Ubuntu 12.04. My daughter's is an older IBM ThinkPad A31 sporting ATI Radeon GFX, and mine is a Toshiba Satellite A100 with Intel GFX. AngryBirds runs fine under WINE 1.5 on mine.

---

