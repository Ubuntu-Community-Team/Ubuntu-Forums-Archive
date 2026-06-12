---
title: "Wine, OpenGL, D3D"
date: 2008-09-16
forum: Wine
---

### Post by tojas on 2008-09-16
Hello!

I have a little problem with my wine, because when I'm trying to start a program with wine I got this error:
> fixme:win:EnumDisplayDevicesW ((null),0,0x33e468,0x00000000), stub!
err:ddraw:IDirectDrawImpl_QueryInterface (0x1345d8) The App is requesting a D3D device, but a non-OpenGL surface type was choosen. Prepare for trouble!
err:ddraw:IDirectDrawImpl_QueryInterface  (0x1345d8) You may want to contact wine-devel for help
err:ddraw:IDirectDrawSurfaceImpl_QueryInterface No interface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
Segmentation fault


Maybe do you know what's the problem? And the solution?

---

### Post by nowshining on 2008-09-16
in the terminal issue the following command:

wine --version

---

### Post by tojas on 2008-09-16
tojas@tojas:~$ wine --version
wine-1.1.4

---

### Post by nowshining on 2008-09-16
ah! i was going to mention using the one from winehq.org but it seems you already have, try removing the dev version and installing the the stable 1.0 version. :)

---

### Post by tojas on 2008-09-16
Maybe... Can you explain me how to do this? :)
Because I installed this version with the help of a tutorial... :)

---

### Post by nowshining on 2008-09-16
open up a terminal:

sudo apt-get remove wine --purge

then download the deb here: i386 for a 32bit OS and amd64 for 64bit OS.

[http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

install..by double-clicking..

edit: it seems like hardy is at the version u got..

try downloading the gutsy version

---

### Post by tojas on 2008-09-16
I tried but when I press double-click then the package installer opens and gives me the error:
> [COLOR="Red"]Error: Dependency is not satisfiable: libldap2[/COLOR]

What's this?

---

### Post by nowshining on 2008-09-16
ah! then try my checkinstall version - it should install without any trouble:

[http://www.4shared.com/dir/7204939/4630f2b9/Gutsy_Hardy__Ubuntu_.html](http://www.4shared.com/dir/7204939/4630f2b9/Gutsy_Hardy__Ubuntu_.html)

---

### Post by tojas on 2008-09-16
Hmm... I installed yours... it installed very well... but I got this error... :(

> tojas@tojas:~/ownstuff/Tibia/TibiaWin/Tibia$ wine Tibia.exe 
Could not load Mozilla. HTML rendering will be disabled.
wine: configuration in '/home/tojas/.wine' has been updated.
fixme:win:EnumDisplayDevicesW ((null),0,0x32e778,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
Segmentation fault


---

### Post by jim_24601 on 2008-09-16
What is "tibia"? It looks as if it's trying to do some Direct3D stuff that isn't supported properly in Wine. Have you tried other apps, i.e. is your Wine setup working OK in general?

---

### Post by argie on 2008-09-16
If it just so happens to be the Tibia MMORPG, they have a Linux client, so don't go trying to run it through Wine.

[http://download.tibia.com/tibia822.tgz](http://download.tibia.com/tibia822.tgz)
[https://secure.tibia.com/account/?subtopic=downloadclient](https://secure.tibia.com/account/?subtopic=downloadclient)

---

### Post by tojas on 2008-09-16
Yea, other win apps work properly... Tibia is a 2D game which uses DirectX or OpenGL for the graphic... Only this app don't want to work...

---

### Post by tojas on 2008-09-16
I downloaded the linux client before the windows... but I got some error... So I read some forum topics and there I found that better to try Win clien with wine...

Here my linux error:
> tojas@tojas:~/ownstuff/Tibia/TibiaLinux$ ./Tibia 
X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  16 (X_GLXVendorPrivate)
  Serial number of failed request:  58
  Current serial number in output stream:  59


Maybe can you help me?:(

---

### Post by jim_24601 on 2008-09-16
Tibia has an AppDB page at [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1563]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1563"). You could try running it with ```
wine Tibia.exe engine 0
``` or ```
wine Tibia.exe engine 1
```

---

### Post by tojas on 2008-09-16
I tried either... but not working... btw with engine 3 working but I got a very blinking window... I can't use it...

---

### Post by aoanla on 2008-09-16
Can you tell us something about your graphics card and the drivers you're using for it?

This looks quite a lot like a driver issue to me.

---

### Post by tojas on 2008-09-16
When I type lspci then I'm getting this list:

> 
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
01:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


But I never installed any drivers... I thought that I need some, but I asked on other topics that what do I need to do to get my graphics card driver but they said that my graphics card driver is automatically installed.

So what do you think about it?

---

### Post by aoanla on 2008-09-17
You have the worst of the Intel built-in graphics solutions, so, yes, your drivers are pretty much built in.

Unfortunately, the Intel 915 series graphics solutions are *horrible* - they don't support a lot of "optional" OpenGL extensions that more recent cards (and even more recent built-in graphics chips) do.
I'm quite prepared to believe that this is the source of your current issues.

I suppose this is a laptop, so you can't go out and spend $30 on a cheap card that actually would work?

---

### Post by tojas on 2008-09-17
Yes... It is a laptop... :( Does it exist any solutions? :(

---

