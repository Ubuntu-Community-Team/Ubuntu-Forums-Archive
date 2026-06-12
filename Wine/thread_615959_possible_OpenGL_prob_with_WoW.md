---
title: "possible OpenGL prob with WoW"
date: 2007-11-17
forum: Wine
---

### Post by RageWarp on 2007-11-17
I get this when i try and run WoW from the terminal

ryan@ryan-desktop:~$ wine "C:\Program Files\World of Warcraft\WoW.exe"
fixme:mixer:ALSA_MixerInit No master control found on Camera, disabling mixer
fixme:advapi:SetSecurityInfo stub
fixme: powrprof: DllMain (0x7d330000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme: powrprof: DllMain (0x7d330000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33ede4,0x00000000), stub!
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl

any ideas?

---

### Post by dhobbs on 2007-11-17
I don't know exactly what's going on but are you trying to run WoW in Wine with DirectX9?  You should be able to force WoW to use OpenGL, which runs fairly well (it's what I use personally).

Here are some links to tutorials that might help.
[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine)
[http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378)

---

### Post by RageWarp on 2007-11-17
well im running dual evga 7600gs cards, so its just a matter of configureing something so i can run it

---

### Post by RageWarp on 2007-11-18
bump

---

### Post by dhobbs on 2007-11-18
Did you look at the links and follow their suggestions?

If you are having problems with DX9 than maybe you could try using OpenGL.  I use OpenGL when I play WoW and it runs great.

---

### Post by RageWarp on 2007-11-18
yes, ive been to those pages before and followed the tutorials but im still getting the same problem

---

### Post by hikaricore on 2007-11-18
> glxinfo | grep rendering

> cat /etc/X11/xorg.conf | grep Driver

Also I'm not sure how well the Linux Nvidia drivers support SLI.  You may want to check on their FAQ.

---

### Post by RageWarp on 2007-11-18
> glxinfo | grep rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

> cat /etc/X11/xorg.conf | grep Drive
        Driver          "kbd"
        Driver          "mouse"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "nvidia"


those are what i got for that

---

### Post by hikaricore on 2007-11-18
There's your problem, as long as direct rendering = No, you will not be able to run and 3d accelerated games/software.

You may want to search around the forums for info on properly configuring Nvidia drivers for SLI and again find out what exactly is supported directly from Nvidia.

---

### Post by RageWarp on 2007-11-19
well ive got the nvidia-settings console up and what not and i dont see any option for sli, and im told that is where it should be unless im missing some necessary driver.

---

### Post by myname on 2007-11-19
I'm not a big nVidia user, but the drivers may not be installed properly, which is the problem I had when I first installed WoW with my ATI card.

what method did you use to install the nvidia drivers?  manual installation, automated via Synaptic, or Envy [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)  which is my personal favorite.

--kevin

---

### Post by RageWarp on 2007-11-19
well ive got it running now, the problem is now that when it does run it doesnt take up the whole screen, it goes kind of into the top left portion of it and when i exit out, it makes a sort of second desktop ontop of my main desktop, anyone know how to fix that?

---

