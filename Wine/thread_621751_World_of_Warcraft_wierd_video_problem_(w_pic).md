---
title: "World of Warcraft wierd video problem (w/ pic)"
date: 2007-11-24
forum: Wine
---

### Post by FlamingGooch on 2007-11-24
Ok I installed WoW and its expansion and when I run the game there's some really wierd almost square like things around the base of all characters in the game. I'll let the pic speak for itself. Anyone have any ideas?

I'm on an ATI X1400 card on my inspiron 9400 notebook, using the flgrx driver and all my 3D desktop effects disabled when running warcraft.

---

### Post by FlamingGooch on 2007-11-26
Anyone have any ideas at all? If there's maybe a command I can type in a terminal that will print out something that will help just let me know.

---

### Post by TidusBlade on 2007-11-26
I really use nVidia and haven't been very secuessful with ATi on ubuntu :\ 
You can try typing "winecfg" in the terminal and try looking around the settings. 
Hope it helps in some way ;)

---

### Post by FlamingGooch on 2007-11-26
I tried looking through the wine configurations but still to no avail. I ran WoW from a terminal and here is the output from opening the game, walking around a little, to closing the game.

devin@devin:~$ wine "C:\Program Files\World of Warcraft\WoW.exe"
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x33ed84,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ecac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f40c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f588,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f580,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f508,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f4f8,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33efe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f124,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:create_server class {bcde0395-e52f-467c-8e3d-c4579291692e} not registered
err:ole:CoGetClassObject no class object {bcde0395-e52f-467c-8e3d-c4579291692e} could be created for context 0x7
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:reg:GetNativeSystemInfo (0x374029c4) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x7d8264a4) stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:win:EnumDisplayDevicesW ((null),0,0x33d1a4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d200,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33de64,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33de64,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33de64,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33de64,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33e164,0x00000000), stub!
fixme:imm:ImmAssociateContextEx (0x20024, (nil), 16): stub
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)


I can't figure out what the very first error I'm getting is but it could be the problem. Also, glxgears works perfectly, however when I type in the terminal ```
glxinfo | grep rendering
``` it returns this:

devin@devin:~$ glxinfo | grep rendering
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)


No idea what the problem is but I want to get the game working as fast as possible.

---

### Post by Sammi on 2007-11-26
> **FlamingGooch said:**
> Also, glxgears works perfectly, however when I type in the terminal ```
glxinfo | grep rendering
``` it returns this:

devin@devin:~$ glxinfo | grep rendering
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

No idea what the problem is but I want to get the game working as fast as possible.It may be that glxgears works, but the graphics card driver is still not doing very well if you're getting a no to direct rendering. ATI simply have not made good drivers for Linux. At least not yet.

Said in plain language: ATI sucks, but Nvidia next time:(

---

### Post by derekr44 on 2007-11-27
Shaders maybe?  Try shutting off the shadows in your graphic settings in-game.  See if that makes a difference.

---

### Post by Ren Höek on 2007-11-28
As you don't have direct rendering, the fglrx module is not loaded properly.
What Version of the ATI driver are you using?
How have you installed it? Just activated the one delivered by Ubuntu, or by downloading from ATI? Wich HowTo?

Please also try:
```
$ cat /var/log/Xorg.0.log | grep "(EE)\|(WW)"
```
and report results.

With some more information we sure can help you.

---

### Post by hotweiss on 2007-11-28
Here are the Cedega WoW hardware notes:

> Some users may get performance increases by disabling AGP FastWrites in their BIOS.

In order to run World of WarCraft in OpenGL mode, you will need to run it with the -opengl commandline option. You will also need to either run X in 16-bit mode, or add the following lines to your WTF/Config.wtf file in the World of WarCraft game directory:

 SET gxColorBits "24"
 SET gxDepthBits "24"

Playing in OpenGL mode may cause the ocean to be black.

ATI users will notice graphical corruption in OpenGL mode. To minimize this, use the GLExtensionBuffer setting in the config file to disable GL_ARB_vertex_buffer_object.

ATI Radeon 9500+ users will notice flickering textures in some areas when using driver version number 8.12.10 or above, and pixel shaders are enabled. Either downgrade to 8.10.19, or disable pixel shaders.

This game should be run in Windows 98 compatiblity mode to ensure that the patches can be installed successfully.

ATI users need to disable Occlusion Queries to be able to play this game in D3D mode.

Due to a hardware limitation we currently recommend using Shader Model 1.4 or less with World of Warcraft. Using Shader Model 2.0 may result in some graphical issues.

Cedega uses wine, so this should help hopefully.

Here's the Wiki:

[http://cedegawiki.sweetleafstudios.com/wiki/World_of_Warcraft](http://cedegawiki.sweetleafstudios.com/wiki/World_of_Warcraft)

I'd seriously consider using Cedega over Wine...

---

### Post by hikaricore on 2007-11-28
> **hotweiss said:**
> 
I'd seriously consider using Cedega over Wine...


I think you should stop giving out bad advice.

Seriously, I'm considering putting up a notice which clearly states NOT to suggest Cedega in the WINE forum at random.

---

### Post by Ferrat on 2007-11-29
> **FlamingGooch said:**
> Ok I installed WoW and its expansion and when I run the game there's some really wierd almost square like things around the base of all characters in the game. I'll let the pic speak for itself. Anyone have any ideas?

I'm on an ATI X1400 card on my inspiron 9400 notebook, using the flgrx driver and all my 3D desktop effects disabled when running warcraft.

I had similar problems in GW with shadows casting from other apps in the background ect. what driver version from ATi are you using, try using 8.40.4 instead of 8.42.3, that helped me

---

### Post by Ren Höek on 2007-11-29
> **hikaricore said:**
> I think you should stop giving out bad advice.

Seriously, I'm considering putting up a notice which clearly states NOT to suggest Cedega in the WINE forum at random.

I agree. The guy has no direct rendering. Spending money for Cedega won't help him. Especially as WoW has gold-status([winehq]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9429")) and is running quite well with wine...

---

### Post by hotweiss on 2007-11-29
> **Ren Höek said:**
> I agree. The guy has no direct rendering. Spending money for Cedega won't help him. Especially as WoW has gold-status([winehq]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=9429")) and is running quite well with wine...

Didn't know about the rule.

---

### Post by hikaricore on 2007-11-29
> **hotweiss said:**
> Didn't know about the rule.

It's not really a rule, but suggesting Cedega to a user who hasn't gotten hardware rendering enabled /w his video device is just one more thing that'll piss them off when it still doesn't work.  It's more like an unspoken rule called sanity and common sense.  ^_^

---

### Post by Sammi on 2007-11-30
@hotweiss
I would like to know what Cedega does better than Wine, and why you think it is worth it to pay 5 bucks a month for it?

It may have a shiny GUI, but seriously, last I checked Cedega was a 5 year old fork of Wine, which has only been updated with lazy hacks, while the serious developers have been working on Wine.

As Cedega is proprietary it can't copy the improvements made to Wine, since wine changed to a free/libre open source license 5 years ago, to prohibit the lazy freeloaders that are Transgaming.

---

### Post by hotweiss on 2007-11-30
> **Sammi said:**
> @hotweiss
I would like to know what Cedega does better than Wine, and why you think it is worth it to pay 5 bucks a month for it?

It may have a shiny GUI, but seriously, last I checked Cedega was a 5 year old fork of Wine, which has only been updated with lazy hacks, while the serious developers have been working on Wine.

As Cedega is proprietary it can't copy the improvements made to Wine, since wine changed to a free/libre open source license 5 years ago, to prohibit the lazy freeloaders that are Transgaming.

Wow, I didn't know that the community here felt that way about Transgaming, although I do understand the animosity.

For me, Warcraft 3 battle.net did not work with wine, yet it worked through Cedega.

---

### Post by John_Henry on 2007-11-30
> **FlamingGooch said:**
> I tried looking through the wine configurations but still to no avail. I ran WoW from a terminal and here is the output from opening the game, walking around a little, to closing the game.

.......................

I can't figure out what the very first error I'm getting is but it could be the problem. Also, glxgears works perfectly, however when I type in the terminal ```
glxinfo | grep rendering
``` it returns this:

devin@devin:~$ glxinfo | grep rendering
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)


No idea what the problem is but I want to get the game working as fast as possible.


You are my Hero,  after having wow work for a while, it suddenly broke on me a few days ago, I have been pulling out my hair....

In the process of making wow work the first time, I had to solved the issue of making 

direct rendering: Yes

So I hadn't though of that as a possible problem. 

I verified that my results to glxinfo were similar to yours, and then fixed the issue by removing glx  (xserver-glx I think its called) 

A nifty looking desktop is cool, but not remotely worth the possibility of messing with my WOW fix.    

Hopefully that will help you.  
If someone comes along who actually knows how to use linux, I wouldnt mind being shown up and finding out how simple it is to have wow AND a nifty desktop ( I miss my embedded terminal)

---

### Post by Sammi on 2007-12-01
> **hotweiss said:**
> Wow, I didn't know that the community here felt that way about Transgaming, although I do understand the animosity.

There is another company that tries to make a profit from the Wine code. That is [Codeweavers]("http://en.wikipedia.org/wiki/Codeweavers"), which makes [Crossover]("http://en.wikipedia.org/wiki/CrossOver"). But in stark contrast to Transgaming, they support Wine both by giving back the code they develop and by employing several of the Wine developers, including the Wine maintainer, Alexandre Julliard, as their CTO. So if you would want to recommend a "for profit" version of Wine, Crossover would be the more political correct, if not also the technically superior one.

Sorry for derailing off the topic.

---

### Post by mad chey on 2007-12-03
Animosity, political correctness, appropriateness, common sence advice aside

i would NEVER recommend cedega over wine, we paid for cedega (had been recommended to us) and played guild wars and then wow on it, and then they updated cedega and suddenly nothing would work as before performance was uber down and you could get no reply from their so called support team, what were we paying for???????

swapped over to wine, and the performance of both games was just phenomenally better and the support is better too!!!!!

---

