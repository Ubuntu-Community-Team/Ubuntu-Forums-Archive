---
title: "World of warcraft starts, plays intro movies then dies"
date: 2008-06-10
forum: Wine
---

### Post by zann00000 on 2008-06-10
As the title says my game starts then the two intro movies and then it just dies. No error or anything the game just stops. Please please help.

---

### Post by wannadumpwindows on 2008-06-10
Did you try to run it from a terminal so you can see if there's any output when it dies?

---

### Post by zann00000 on 2008-06-10
Im sorry i am really new to ubuntu. How do i run it in the terminal?

---

### Post by wannadumpwindows on 2008-06-10
Take a look here. 

[https://help.ubuntu.com/community/WorldofWarcraft]("https://help.ubuntu.com/community/WorldofWarcraft")

It's a long read, but it should tell you everything you need to know.

P.S. To open it in a terminal, go to 

Applications >> Accessories >> Terminal

Then, in the window that pops up, enter this command:

```
wine "C:\Program Files\World of Warcraft\WoW.exe"
```

---

### Post by zann00000 on 2008-06-10
I havn't been able to find any where in thier about my specifict problem. 

zann00000@zann00000-laptop:~$ wine "C:\Program Files\World of Warcraft\WoW.exe"
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7bf30000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7bf30000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x32ede4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32ece0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f328,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f05c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f6ec,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x138770) call to IWineD3DDevice_CreateQuery failed
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x136b50) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x32f05c,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
Mesa 7.0.3-rc2 implementation error: i915_program_error: Exceeded max nr indirect texture lookups
Please report at bugzilla.freedesktop.org
DRM_I830_CMDBUFFER: -22

---

### Post by zann00000 on 2008-06-10
That was what came up when i ran it in terminal.

---

### Post by wannadumpwindows on 2008-06-10
I'm not sure on the specifics, but there are a couple errors in there. Something isn't happening right. Did you take a look at the link? You can read through the steps and see if there's anything you missed when you installed.

---

### Post by zann00000 on 2008-06-10
I am 110 percent shure i did it right. I have already installed it on desktop works like a dream and i have reinstalled it 3 times. I dont know but it could have something to do with when i install it saying that i have not enough ram (512), but my computer did the same thing when i was running windows and i have exactly that amount of ram. I kind of think it may have somthing to do with my graphics card. If you have any ideas...

---

### Post by wannadumpwindows on 2008-06-10
Not really, I'm not very familiar with it. More ram would help for sure. It should still run though. Even if it would be slow. I'm guessing it's just a minor step you might have missed or something. Do you have a 3D capable graphics card set up with the right driver for your card?

---

### Post by zann00000 on 2008-06-10
how would you check that (the graphics cards)


Thier are not many things i feel very confident when it comes to ubuntu, but i am pritty shure i installed it the same way as before. 

I also used to have a problem when i played wow where i would get the blue screen of death until some one had me type in /somthing 0 in the game. Sry i couldnt be more specific it was a while ago.

---

### Post by hyper_ch on 2008-06-10
you have direct rendering?

```

glxinfo | grep rendering

```

If so, then it might be the ram.

---

### Post by zann00000 on 2008-06-10
It does come up saying yes. If it is the ram is thier any way of toning down the game so I can get it to work. Cuase once u do have it up you cant go to the control panal and turn down graphics and what not and its plays much faster.

---

### Post by hyper_ch on 2008-06-10
I play WoW on 1 GB with my 128 mb video card... it runs fine...

---

### Post by thisismalhotra on 2008-06-10
to check your video card run

```
lspci
```

---

### Post by zann00000 on 2008-06-13
I GOT

zann00000@zann00000-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
06:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by thisismalhotra on 2008-06-13
Intel Corporation Mobile 915GM/PM/GMS/910GML

^this is your graphics card.

Anyways I dont know if you have been to this links before but follow instructions on this link and see how it goes for you.

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)

---

