---
title: "The Elder Scrolls III: Morrowind - WINE errors"
date: 2011-11-24
forum: Wine
---

### Post by Starminn on 2011-11-24
So I was feeling nostalgic after seeing multiple videos of graphics overhauls for Morrowind, and decided I wanted to play it once more.

I fire up the Setup.exe in WINE, follow all the configuration steps outlined here: [http://www.uesp.net/wiki/Morrowind:Linux](http://www.uesp.net/wiki/Morrowind:Linux), as well as on the WineHQAppDB here [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3329](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3329) then run "Morrowind Launcher.exe"

What happens is, the "splash screen" appears, with options to Play, Data Files, Options, etc., so I hit "Play" (note: all following information also occurs if I skip the Launcher and just launch "Morrowind.exe" in WINE).

What happens next is apparently beyond my ability to solve -- a small window titled "Morrowind" pops up, and a dialog box stating, 'Render creation error: "Unknown stencil mode format."'

I've tried many attempts at solving this problem to be found on this forum, but alas I have not found one that works. I have also tried running this in PlayOnLinux (since it has Morrowind listed already), but it made no difference, and I'd like to simply focus on pure-WINE way.

System specs:
OS: Ubuntu 11.10, Oeneric Ocelot - Unity DE - 32-bit
System RAM: 4.5GB
Processor: Intel® Pentium(R) 4 CPU 3.00GHz × 2
Video Card: ATI Radeon X600, 128MB RAM
WINE version: "wine-1.2.3" (from command 'wine --version')


Being run in a Terminal:
```
robert@robert-Dell-DME510:~$ cd /home/robert/.wine/drive_c/Program\ Files/Bethesda\ Softworks/Morrowind
robert@robert-Dell-DME510:~/.wine/drive_c/Program Files/Bethesda Softworks/Morrowind$ wine Morrowind\ Launcher.exerobert@robert-Dell-DME510:~/.wine/drive_c/Program Files/Bethesda Softworks/Morrowind$ err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 968
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32_FLOAT with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:win:EnumDisplayDevicesW ((null),0,0x33ee90,0x00000000), stub!
```

(cd into the installed WINE directory; launch the Morrowind Launcher.exe; hit "Play"; that's when the "err:d3d:check_fbo_compat..." displays.)

It would appear that "d3d" is in reference Direct3D; however I have no idea how to go about solving this problem.


Lastly, here are some screenshots:
[IMG]http://imagebin.org/185419[/IMG]
(That's the Launcher. - [http://imagebin.org/185419](http://imagebin.org/185419))

[IMG]http://imagebin.org/185420[/IMG]
(That's after hitting "Play" or launching "Morrowind.exe". - [http://imagebin.org/185420](http://imagebin.org/185420))

---

### Post by zomgneeks on 2011-11-24
I'm getting the same exact error after updating to 11.10.

---

### Post by Rubi1200 on 2011-11-25
Moved to Wine sub-forum.

Thanks for understanding.

---

### Post by Starminn on 2011-11-25
Thank you, Rubi. I was a bit unsure about where to put it. I wasn't aware there was a wine category -- I'll keep that in mind for future reference.

---

### Post by Starminn on 2011-11-30
Bump for support. If anybody has a suggested fix, I'd be more than happy to hear it. :)

---

### Post by Dlambert on 2011-11-30
Try : > 
[LIST]
[*] Use of dll overrides "devenum.dll" and "dxdiagn.dll" may be necessary for the game to run.
[*] Requires using winetricks to install directx9 and vcrun2005.
[*] The  following registry key changes are recommended (Use the command "wine  regedit" and then add them as strings to the appropriate directory):
[/LIST]
[LEFT][HKEY_CURRENT_USER\Software\Wine\Direct3D]
OffscreenRenderingMode = fbo
UseGLSL = enabled
VideoMemorySize = 256
You may also put in whatever amount of memory your video card uses instead of 256.
[/LEFT]

[LIST]
[*]To  get the autoupdater to run, right click anywhere on the autoupdate  window (except the status text part), and then click "dedicated internet  connection". It should now work.
[*]If you are unable to  change resolution while using fullscreen mode, emulating a virtual  desktop may be useful for getting the game to allow other resolutions.
[/LIST]
[IMG]http://appdb.winehq.org/images/blank.gif[/IMG]

---

### Post by Dlambert on 2011-11-30
Install proprietary drivers?

---

### Post by Dlambert on 2011-11-30
Others have reported that installing directx using windtricks has solved the problem.

---

### Post by Starminn on 2011-12-17
I have installed DirectX9 using Winetricks, but to no avail. The same issue still persists.

---

### Post by WienerWuerstel on 2011-12-17
I had some Problems with Morrowind too but then I put the MSVCP60.DLL in the Folder where the Game is installed and it worked. Google can help you where to find the MSVCP60.DLL File.

---

### Post by Dlambert on 2011-12-17
> **WienerWuerstel said:**
> I had some Problems with Morrowind too but then I put the MSVCP60.DLL in the Folder where the Game is installed and it worked. Google can help you where to find the MSVCP60.DLL File.

Could try OpenMW. [http://openmw.org/]("http://openmw.org/")

---

### Post by Starminn on 2011-12-17
wiener: I tried that but it had no effect.

Dlambert: I read about that on Omg!Ubuntu, and is actually the reason I wanted to try playing Morrowind again. At the time OpenMW had practically no textures, but I guess my options right now are essentially play that as it is now, or just wait for it to come further along.

I'll probably just start playing OpenMW - at least I can help with dev/bugs, etc. that way.

Thank you for everyone who tried helping me though. I'm just going to go ahead and mark this issue as Resolved.

---

### Post by Dlambert on 2011-12-17
> **Starminn said:**
> wiener: I tried that but it had no effect.

Dlambert: I read about that on Omg!Ubuntu, and is actually the reason I wanted to try playing Morrowind again. At the time OpenMW had practically no textures, but I guess my options right now are essentially play that as it is now, or just wait for it to come further along.

I'll probably just start playing OpenMW - at least I can help with dev/bugs, etc. that way.

Thank you for everyone who tried helping me though. I'm just going to go ahead and mark this issue as Resolved.

I'm Sorry I couldn't help!

---

### Post by Starminn on 2012-11-03
Thought I might post my solution here for others looking:

In winecfg ("Configure Wine")->"Libraries"->"New override for libraries"->"quartz"->set it to "builtin"

It made everything automagically work for me. :)

---

### Post by XXAzJcX on 2013-09-10
For future reference, I can confirm that the above worked for me as well.

---

### Post by stephen30096 on 2014-08-16
Hi, im trying to run morrowind, but im getting that Stencil error and trying that quartz library builtin did not help. Could someone please help?

---

