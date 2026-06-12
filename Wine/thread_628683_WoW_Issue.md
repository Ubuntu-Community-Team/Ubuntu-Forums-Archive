---
title: "WoW Issue"
date: 2007-12-01
forum: Wine
---

### Post by melzanis on 2007-12-01
Ok I don't know what is up but I can't even get into WoW, I use the command I always use wine "C:\Program Files\World of Warcraft\WoW.exe" -opengl and it keeps spitting out this error junk:
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl
everything is installed right, I have all the updates. I don't know what to do, can some please give me a hand with 

cheers

---

### Post by cogadh on 2007-12-01
Try changing directories to the game's install directory, then run the executable:
```
cd .wine/drive_c/Program\ Files/World\ of\ Warcraft/
wine WoW.exe -opengl
```
Also, have you checked the existing WoW how-to thread for help?
[http://ubuntuforums.org/showthread.php?t=579378](http://ubuntuforums.org/showthread.php?t=579378)

---

### Post by melzanis on 2007-12-02
hey cogadh, 
      Thanks for the reply. I tried what you said and sadly it's still not working. I get the same output from before. 

[email]warlock@warlock-desktop:~/.wine[/email]/dosdevices/c:/Program Files/World of Warcraft$ wine WoW.exe -opengl
fixme:advapi:SetSecurityInfo stub
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 480, std (d/m/y): 4/11/2007, dlt (d/m/y): 11/03/2007
fixme:powrprof:DllMain (0x7d610000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d610000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed84,0x00000000), stub!
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl

---

### Post by cogadh on 2007-12-02
Something is not right about where you ran that from. It looks like you went into the game's install directory by following the symbolic link in the "dosdevices" directory. I'm not sure that will actually work correctly. Make sure you run the commands exactly as I posted them.

---

### Post by melzanis on 2007-12-02
Still didn't work. I'm getting the same output as the other two tries =(

---

### Post by TerraRoot on 2007-12-12
I get the same errors when trying to run gta-vc, and none of my other games work either.
Seems like something is wrong in my installation of ubuntu and not wine.

---

### Post by cogadh on 2007-12-12
Have you installed the proper driver for your video hardware? The default drivers in Ubuntu can't do 3D acceleration and could produce those types of errors.

---

### Post by TerraRoot on 2007-12-12
Nvidia drivers are installed, i bet it's a compiz/xgl problem

---

### Post by melzanis on 2007-12-12
ok i've uninstalled everything, then reinstalled Wine. But now i'm getting the following error message:

[email]warlock@warlock-desktop:~/.wine[/email]/drive_c/Program Files/World of Warcraft$ wine WoW.exe -opengl
fixme:powrprof:DllMain (0x7d680000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation semi-stub: SystemPowerCapabilities
fixme:powrprof:DllMain (0x7d680000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x34f230,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34eee0,0x00000000), stub!
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl

you know ever since 7.10 game out i've lost everything I had installed. And I can't seem to find anything that works anymore. I don't know what else to do can some please help me with this problem. 

cheers

---

### Post by hikaricore on 2007-12-12
melzanis: Did your upgrade go well or wrere there errors?  If you didn't upgrade and installed from scratch however I'm sure the reason things are missing is obvious.

You may want to check that your video drivers are properly installed?

---

### Post by melzanis on 2007-12-13
I'm not sure where and how to check my video drivers. I have my restricted drivers are installed. When I installed the 7.10 from the 7.04 it was from the upgrade app that shows up. the only thing is that upgrade app said that it was going to uninstall a bunch of lib????? packages and my beryl stuff too. 

      I just need to get this stuff fixed. I will repost the error message when I go to run WoW from the terminal:

[email]warlock@warlock-desktop:~/.wine[/email]/drive_c/Program Files/World of Warcraft$ wine WoW.exe -opengl

fixme:powrprof:DllMain (0x7d690000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation semi-stub: SystemPowerCapabilities
fixme:powrprof:DllMain (0x7d690000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x34f230,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34eee0,0x00000000), stub!
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl

I really don't know what all that means. help me please

---

### Post by hikaricore on 2007-12-13
You may need to inform us of exactly what video hardware you're using.

The drivers may not be installed properly, as WINE is outputting errors (the only 3 actual erros) about OpenGL compatibility at the bottom.

---

### Post by melzanis on 2007-12-13
I'm using the Asus nvidia GeForce 7300GS video card, so the Nvidia drivers. if any further spec's are needed just let me know.

Cheers

---

### Post by cogadh on 2007-12-13
Which Nvidia drivers? The default from the repos (nvidia-glx or nvidia-glx-new), the ones from the Nvidia website or the generic "nv" driver that is installed by default in Ubuntu?

---

### Post by melzanis on 2007-12-13
The only drivers that I can see in the synaptic manager are the nvidia-glx driver. I also have the restricted drivers turned on too. do I need any other nvidia driver in the synaptic manager installed?

Sorry I should have said that I have nvidia-glx installed and no other driver installed, other then the restricted drivers that are turned on.

---

### Post by chadlongstaff on 2007-12-16
I'm having the same problem with Half Life 2 on Steam; Steam runs fine but as soon as I try to launch a game I get the same sequence of errors. Running gutsy, wine 0.9.50 and nvidia drivers version NVIDIA-Linux-x86-100.14.19-pkg1.run. Any help appreciated.

---

### Post by melzanis on 2007-12-17
Ok I want to start off by saying... i'm sorry for any language that I use, but my frustration needs to be voiced. 

For the past week I have had nothing but problem with this ******* wine app. However this all started the minute I upgraded to 7.10. Everything was working so nice, I could play the games that I installed. I never got any error message. But now I can't ******* do a damn thing. I was forced to wipe out my harddrive and reinstall Ubuntu 7.04. Only because that was the version that worked for me. However, i'm faced with the same damn problems as before. Even after install Warcfraft 3 (which the installation went smooth the hole way) I can't play the damn game. I don't know if after install wine and then going into winecfg, if there is anything I have to do with the libraries or what because I don't have anything in that tab. I'm getting to the point where Windows sounds pretty ******* good right now... And I ******* hate Windows. Now I have followed all the threads that tell me how to install wine. Yet it still doesn't work. So I don't know what more to do, if any one out there nows what I should do with wine to get it to work. Please let me know, because I don't know what to do any more.

Thanks a million

---

### Post by melzanis on 2007-12-19
Well I don't know hot to explain this other then I fixed the problem. It was a bit extreme but it worked. 
       After reinstalling Ubuntu 7.04 for a second time, I said to myself I should just upgrade to 7.10 gutsy. Shortly after the upgrade (by the way was done through the upgrade-manager) was finished I installed wine. I worked through the walk-through at WineHQ (link to site: [http://www.winehq.org/site/download-deb]("http://www.winehq.org/site/download-deb") ). 
      There after I used the the WoW thread to install the game and any tweaks needed. Sure enough the game was working just fine. I just want to thank every one that put their time and effort into helping me fix this problem.

Cheers

---

