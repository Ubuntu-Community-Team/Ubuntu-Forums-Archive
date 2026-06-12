---
title: "x86-64, Edgy, Wine, and WoW - Help :("
date: 2007-02-09
forum: x86 64-bit Users (Pre April '08)
---

### Post by jat850 on 2007-02-09
Hello all,

I am trying to make the final stages of my switch from Windows to Linux and am very pleased with Ubuntu so far.

I installed 6.10 (Edgy) using an x86_64 kernel, 2.6.17-10.  Because I am using a SATA raid, I had to do some convoluted manual steps to get dmraid/fakeraid working, but finally I have a working ubuntu desktop system - X11 works, all my "normal" applications work, I even got Firefox32 installed so that I could use the Flash player plugin according to some useful help on the forums.

My last step was to get WINE working for a few important leftover programs from my Windows desktop - namely Pokerstars and World of Warcraft.

I compiled and installed WINE 0.9.30 and had it running, no hitches, and was able to install/run PokerStars with no problems whatsoever... because of this, I'm fairly confident my WINE install was successful (and as far as I know, PokerStars.exe is a 32-bit application so it is running 32-bit compiled apps no problem).

However, I've had no luck with World of Warcraft and I can't figure out why.

I'm running the latest nVidia drivers - 97.xx - compiled and installed from the website.  I am pretty sure that is working properly as well, because glxgears runs properly, and I installed and tried Beryl and it worked properly as well.

I have tried WoW in D3D and OpenGL mode - in D3D mode it will launch (but crash when the loading screen begins), and with OpenGL I get this error:

```
jeremy@ubuntu:~/.wine/drive_c/Program Files/World of Warcraft$ wine WoW.exe -opengl
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:powrprof:DllMain (0x7e1b0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7e1b0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33edd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f33c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f544,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  29 ()
  Serial number of failed request:  420
  Current serial number in output stream:  420

```

Can anyone help me sort this out?  Or if this is the wrong place to ask, redirect me to the proper forum?  Thank you.

---

### Post by jat850 on 2007-02-09
**** UPDATE ****

For anyone else running into the same problems I have, I have fixed this!

I discovered that even though glxinfo indicated that Direct Rendering for OpenGL was working, it in fact was not.  I thought perhaps it was a driver issue, or that for some reason my nVidia drivers did not install properly - even though it appeared everything was working as it should have.

So I downloaded an archive version of the nVidia drivers and went to 87.76 (the x86_64 version, still), and installed them.

Within seconds, I ran my direct rendering test (it passed) and within 5 seconds after that, I was launching WoW successfully using WINE.

It runs beatifully.

---

### Post by buMPer on 2007-02-12
> **jat850 said:**
> **** UPDATE ****

So I downloaded an archive version of the nVidia drivers and went to 87.76 (the x86_64 version, still), and installed them.

Within seconds, I ran my direct rendering test (it passed) and within 5 seconds after that, I was launching WoW successfully using WINE.

It runs beatifully.

used to have the same problem.  this is what i did:

1.  i ran the latest nvidia installer 
```
sudo sh NVIDIA-Linux-x86_64-1.0-9746-pkg2.run -x
```but instead of installing i just extracted the files using the -x switch. 

2.  look for the "nv" folder in the extracted files in /usr/src/nv and move the whole "nv" folder to /usr/src folder ```
sudo mv -df nv /usr/src 
```

3.  uninstall the existing nvidia driver including the nvidia-kernel using synaptic

4.  follow the procedure in compiling and installing the module found inside the "nv" folder

```
sudo make module
```
```
sudo make install
```

5. after a successful module install, do a "ctrl+alt+F3" and log in

6. stop the xwindow
```
sudo /etc/init.d/gdm stop 
```

7.  run the latest nvidia installer and follow the instructions.  just hit enter all the way for questions/confirmations that will pop-up during the install process
```
sudo sh NVIDIA-Linux-x86_64-1.0-9746-pkg2.run
```

8.  after installation go back to desktop
```
 sudo gdm 
```

halflife 2 and CS source runs smoothly using wine and latest nvidia drivers

---

### Post by dominicd on 2008-02-20
Thanks buMPer! That did it for me =D
Thanks a lot mate =)

PS: Don't forget to reinstall your kernel

```
sudo apt-get install linux-headers-$ (uname -r) build-essential
```

---

