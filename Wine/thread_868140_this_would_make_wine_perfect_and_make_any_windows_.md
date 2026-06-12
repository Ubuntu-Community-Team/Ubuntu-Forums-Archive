---
title: "this would make wine perfect and make any windows game run"
date: 2008-07-23
forum: Wine
---

### Post by kielanmatt on 2008-07-23
i need to say that if we want games on linux we should form a multi distro community (get developers of linux distro's working together) then we could talk about accelarating the systems architecture and make a gaming distro or a package that would:

-tweak your system to drop the window manager's effects without you doing it automatically (disabling beryl and starting it after you close the app)
- make launching new X sessions on display 3 easier (i fail all the time)
-tweak wine to its absolute extents

Secondly we would establish a close partnership with wine so the kernel and wine would become even more bound (so quicker, correct me if im wrong) also WINE should have an option of disabling/enabling certain registry keys for certain apps. WINE should have a perfect compatibility layer between OpenGL=Directx(graphic files)
ALSA(in some cases OSS)=DirectX(sound files). ALSO some work in the direction of giving games some form of direct acces to devices would solve some problems.

I have a thought of maybe WINE should get the windows drivers (the ones that come on CD for graphic cards and audio cards) and use them for games (if you enable windows driver mode) and then the X display stops and there is only one display session for WINE's emulated desktop(if you wanted to run an app along with the game e.g. music player) or just the app. The downsides of this is that all aps like XMMS (ones that you switched on before the game starts) would not play the music (cause only one driver can acces the same device at once) and display any picture. But then when youre finished with playing either WINE would automatically detect you closing the app and run
Code:

/etc/init.d/gdm start

(plus some commands for loading the drivers again) or you would have to do it manually Ctrl+Alt+Backspace
Code:

/etc/init.d/gdm start

and youre done back on ubuntu with the ubuntu drivers loaded back

well i wanted to say that this kind of situation would be very system resource efficient (linux itself uses about 1% of ram on my commy, imagine the number it would use without gdm and graphics, also think about this comparing to windows) because less than 1% of sys resources (i might be wrong but those are my results for the ram test for my commy) THE SYS REQUIREMENT OF GAMES PLAYED UNDER WINE WOULD LOWER BY A LOT SO IF YOU NEED 1.6 Ghz to run a game you can make it with 1.5 on WINE OR if you need 1.5GB of RAM to run summink under ViSTa then you will get away with half of it or 1GB(probably)

---

### Post by hessiess on 2008-07-23
you do not want to murge wine with the kernal, doing so would open the posibilaty of running windows virases on Linux, bloat the kernal, and probaly decrese system stabilaty. Linux is stable BECOUSE EVERYTHING IS MODULAR.

---

### Post by kielanmatt on 2008-07-23
bad idea sorry but i am thinking about letting WINE use windows drivers and ubuntu drop its own ones down, So windows games run on windows drivers and on directx libraries not like its now

       ________}SOUND----WINEDirectX---ALSA---DEVICE
Game--{________
               }GRAPHICS---WINEDirectX---OPENGL---NVIDIA_LINUX_DRIVER---GPU

basically very hard to achieve hardware acceleration

---

### Post by hessiess on 2008-07-23
the kernals are completly difarent,( hybrid(win) vs monolithic(linux)) the only way a win driver could run on linux would be through an emulater, or compatabilaty layer. theraticly it would be posable to impliment directx native on Linux, but its cloesd source so isnt going to happen.

---

### Post by ad_267 on 2008-07-23
> **kielanmatt said:**
> -tweak your system to drop the window manager's effects without you doing it automatically (disabling beryl and starting it after you close the app)


I wrote a bash script that does that here: [http://ubuntuforums.org/showthread.php?t=867562](http://ubuntuforums.org/showthread.php?t=867562)

I don't think that embedding wine into the kernel or making it a kernel module would be a good idea. Wine is only a temporary solution, the real solution will be increased support for Linux from software developers.

A way to easily launch an xsession for only running a game could be useful though and free up a lot of resources. I'd be interested if there's an easy way to do this.

---

### Post by kielanmatt on 2008-07-23
what im on about is letting WINE install Windows drivers and if you supply your password WINE would switch off the ubuntu drivers (casting ubuntu aside thats what i would say) and use the Windows ones so directx runs normally (cause it reffers to Windows drivers not emulated drivers and behind linux drivers)

What im on about is turning WINE into almost a mini-gaming-windows-clone (i know a total clone is not possible) so it runs directx just like winXp on VMware but with DIRECT DEVICE ACCESS (and because two drivers cannot control the same device at once one of them has to be unloaded, the ubuntu one) and the drivers that WINE would use would be windows ones that you download from nvidia.com for example

---

### Post by hessiess on 2008-07-23
windows drivers ARE NOT comaptable with the linux kernal. it is imposable to 'just switch the drivers'

---

### Post by mad_golfer on 2008-07-23
If wine and kernal are merged then windows may start infecting linux. 

Very Bad !!!

- Anthony
[Found a great deal on PC Magazines]("http://www.magazinesusa.com/pc-magazine-subscription.cfm") :lolflag::guitar::):KS

---

### Post by Hazer on 2008-07-24
everything else is cool except wine integration into the kernel,

because Linux achieves great stability by having separate modules rather than integration into the kernel.

Also, if exe files could be run native, then windows viruses would infect Linux! Uncool!

---

### Post by kielanmatt on 2008-07-24
not native div im just talking about windows drivers being loaded native

---

### Post by aoanla on 2008-07-24
> **kielanmatt said:**
> not native div im just talking about windows drivers being loaded native

Yes, and as two people have already mentioned, the linux kernel is not equivalent to the windows kernel. It would be astonishingly difficult to provide support for kernel-level shims to allow windows drivers to talk to the linux kernel, and also totally wasteful of effort - there's a lot of device drivers already native to linux, especially in the domain of graphics and sound devices, which is most useful to gamers.
I think you've slightly misinterpreted the intent of Wine as a project...

---

### Post by kielanmatt on 2008-07-24
im not talking about the nativity of drivers but that directx is not native to linux drivers,

anyway no one would ever do this

---

### Post by aoanla on 2008-07-24
> **kielanmatt said:**
> im not talking about the nativity of drivers but that directx is not native to linux drivers,

No, it isn't. But your statement refers to Wine "switching off" the "ubuntu drivers" and loading Windows drivers. It's very obvious that implementing this would require either an entirely new kernel (which wouldn't be linux anymore), or the development of an extensive shim structure far beyond the scope of Wine itself.
What Wine currently does is to map DirectX calls onto OpenGL calls, which it would still have to do even *with* Windows drivers loaded, since there's no linux native DirectX, either...

What we're saying here, politely, is that your idea sounds "cool", but is almost certainly more complex for less gain than the approach Wine currently adopts.

---

### Post by cyclobs on 2008-07-25
couldn't someone develop a virtualization program that will allow us to run games from a windows install on the main linux desktop (so it runs as if you are playing it on ubuntu) and have the game run through the nvidia drivers. so some way make windows drivers to run on the linux drivers. if that makes sense

---

### Post by naz37 on 2008-07-25
OK to settle a few issues here,

Wine using Windows drivers;
This has in effect already been done. Checkout [ReactOS]("http://www.reactos.org/en/index.html") it aims to be a open source version of windows that's binary compatible with windows XP. So you could in theory run any game on it and use windows drivers.

Merging Wine and Linux kernel;
A Chinese tech company is in the process of doing just this, they are calling it the "Unified-kernel". Its is a mash up of wine, ReactOS and the Linux kernel. Basically it would be able to run Windows and Linux app using both Windows and Linux drivers. There a interesting [thread]("http://forum.winehq.org/viewtopic.php?t=93&highlight=unifiedkernel") on it at the winehq forums

Both have "working" alphas out if anyone wants to try but id recommend doing it in a virtual machine.

---

### Post by aoanla on 2008-07-25
Indeed. But neither "Unified-kernel" nor ReactOS are within the scope of Wine, or Linux for that matter. Which is the point...

---

### Post by Viranh on 2008-07-27
I found a thread that has a script for launching a new xsession: [http://ubuntuforums.org/showthread.php?t=634067](http://ubuntuforums.org/showthread.php?t=634067). I hope this helps.

---

### Post by HeadHunter00 on 2010-02-12
> **ad_267 said:**
> I wrote a bash script that does that here: [http://ubuntuforums.org/showthread.php?t=867562](http://ubuntuforums.org/showthread.php?t=867562)

I don't think that embedding wine into the kernel or making it a kernel module would be a good idea. Wine is only a temporary solution, the real solution will be increased support for Linux from software developers.

A way to easily launch an xsession for only running a game could be useful though and free up a lot of resources. I'd be interested if there's an easy way to do this.
I love you man.

---

