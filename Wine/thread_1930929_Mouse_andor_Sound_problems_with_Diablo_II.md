---
title: "Mouse and/or Sound problems with Diablo II"
date: 2012-02-24
forum: Wine
---

### Post by Wraakvol on 2012-02-24
Hello, guys!

I bought Diablo II and its extension recently, and I installed on my laptop using Wine. Quite tricky the installation process with the multiple discs, but I installed the game at last.

The problems start when I run Diablo II using Wine, whether I run it in fullscreen mode, or windowed. So, let's begin:

**Fullscreen Mode:**

Prologue cinematics always sound, but when I enter the first screen, there are 2 choices:

[LIST]
[*] Sounds perfectly ambiance and voices, but the mouse jumps when I move the cursor or I click the screen.

[*] Doesn't sound at all, and the mouse jumps when I move the cursor or I click the screen.
[/LIST]

I googled a while, trying to get a solution, but nothing came to light. Maybe I didn't searched enough. But anyway, I decided to run Diablo II windowed, to see if I could play it normally, but...

**Windowed Mode:**

[LIST]
[*] The mouse works perfectly, but the sound doesn't. It plays the background music in the main screen, but when I start to play the sounds goes away.

[*] The mouse works perfectly, but the sound doesn't work at all, 'cause as I start the game, there's no sound.
[/LIST]

I use Ubuntu 11.10, and my Wine version is 1.3.28. What says the terminal while I'm running the game? Let's see...

**Fullscreen Mode:**

```
wraakvol@AsgeirrCorp:~$ wine /home/wraakvol/.wine/drive_c/Program\ Files/Diablo\ II/Game.exe
fixme:advapi:SetSecurityInfo stub
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 240, std (d/m/y): 11/03/2012, dlt (d/m/y): 14/10/2012
fixme:win:EnumDisplayDevicesW ((null),0,0x32e9e8,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d_surface:wined3d_surface_flip Ignoring flags 0x1.
err:xvidmode:ComputeGammaFromRamp ramp not uniform (max=0.877252, min=0.004487, avg=0.363268), rejected
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 4 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x4275a90,0x427ea7c): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x4275a90,0x427ea7c): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x4275a90,0x427ea7c): stub
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
err:xvidmode:ComputeGammaFromRamp ramp not uniform (max=0.877252, min=0.004487, avg=0.363268), rejected
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
err:ddraw:ddraw_surface7_Flip Can't find a flip target
err:ddraw:ddraw_surface7_Flip Can't find a flip target
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
err:xvidmode:ComputeGammaFromRamp ramp not uniform (max=0.877252, min=0.004487, avg=0.363268), rejected
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
err:xvidmode:ComputeGammaFromRamp ramp not uniform (max=0.877252, min=0.004487, avg=0.363268), rejected
err:xvidmode:ComputeGammaFromRamp ramp not uniform (max=0.877252, min=0.004487, avg=0.363268), rejected
err:xvidmode:ComputeGammaFromRamp ramp not uniform (max=0.873086, min=0.010148, avg=0.365768), rejected
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
err:xvidmode:ComputeGammaFromRamp ramp not uniform (max=0.877252, min=0.004487, avg=0.363268), rejected

```

**Windowed Mode:**

```
wraakvol@AsgeirrCorp:~$ wine /home/wraakvol/.wine/drive_c/Program\ Files/Diablo\ II/Game.exe -w
fixme:advapi:SetSecurityInfo stub
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 240, std (d/m/y): 11/03/2012, dlt (d/m/y): 14/10/2012
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 4 channels, pretending there's only 2 channels
fixme:alsa:AudioClient_GetMixFormat Don't know what to do with 32 channels, pretending there's only 2 channels
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x16f9c8,0x1789b4): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x16f9c8,0x1789b4): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x16f9c8,0x1789b4): stub

```


So, as you see, I haven't enjoyed my game so far. And I really don't want to think I've wasted &#8364;15 for nothing.

Any ideas, or suggestions?

---

### Post by Soulcage on 2012-02-25
I recommend you try using a glide wrapper [http://www.svenswrapper.de/english/index.html]("http://www.svenswrapper.de/english/index.html")
Extract the files into your diablo II folder then run the exe, select to run using desktop resolution. Then run the diablo II video test and select glide.
I don't know if it will solve your problem, but you can try anyways.

You may also want to try running the latest version 1.4-rc5

---

### Post by Wraakvol on 2012-02-25
Soulcage:

I tried your solution and... it didn't work at all! :lolflag:

I attach what error gave me (.jpg file), and what the terminal said:

```
wraakvol@AsgeirrCorp:~$ wine /home/wraakvol/.wine/drive_c/Program\ Files/Diablo\ II/glide-init.exe 
fixme:dwmapi:DwmIsCompositionEnabled 0x3dced1
fixme:dwmapi:DwmEnableComposition (0) stub
wine: Unhandled exception 0xc0000090 at address 0x6bdd7c02 (thread 0009), starting debugger...
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 240, std (d/m/y): 11/03/2012, dlt (d/m/y): 14/10/2012
Process of pid=0008 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
wraakvol@AsgeirrCorp:~$ process  tid      prio (all id:s are in hex)
0000000e services.exe
	0000001a    0
	00000014    0
	00000010    0
	0000000f    0
00000011 winedevice.exe
	00000016    0
	00000013    0
	00000012    0
00000017 plugplay.exe
	0000001b    0
	00000019    0
	00000018    0
0000001c explorer.exe
	0000001d    0
You must be attached to a process to run this command.
No process loaded, cannot execute 'detach'

```

So, here we are again... :?

I think if I run an older version of Wine maybe the test (and hopefully the game) will run without problems. Anyway, I'll try it tomorrow, after my breakfast. :P

Newbie question: Should I report it?

---

### Post by Soulcage on 2012-02-26
Sometimes that glidewrapper gets broken then eventually fixed, oh well probably wouldn't of helped anyways.

---

### Post by Wraakvol on 2012-02-28
Well, I played Diablo II in windowed mode last night and 5 minutes ago, and it works perfectly. I don't know what did I change, though. :lolflag:

In full-screen I have the same problem as I mentioned, so, I'll just play it as I did: windowed.

PS: I love how sounds in French... Diablo, le Seigneur de la Terreur... :cool:

---

