---
title: "Trying to run OnLive, no window appears. (11.10 x64 Atom cpu)"
date: 2011-12-10
forum: Wine
---

### Post by achoo5000 on 2011-12-10
I don't even get an OnLive login screen. When I run the program, the cpu pegs at 100% and nothing happens.

Here's some setup info: Ubuntu 11.10 x64 running on Intel Atom netbook.

Here's the output of wine:
```
wine: cannot find L"C:\\windows\\system32\\winemenubuilder.exe"
err:wineboot:ProcessRunKeys Error running cmd L"C:\\windows\\system32\\winemenubuilder.exe -a -r" (2)
fixme:toolhelp:CreateToolhelp32Snapshot Unimplemented: heap list snapshot
fixme:toolhelp:Heap32ListFirst : stub
fixme:dwmapi:DwmIsCompositionEnabled 0xc2f35c
fixme:wbemprox:wbem_locator_ConnectServer 0x1359f0, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0xc2f140)
fixme:xinput:XInputEnable (1) Stub!
fixme:xinput:XInputGetCapabilities (0 0 0xc2f2b8)
fixme:win:RegisterRawInputDevices RIDEV_INPUTSINK support is not implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x160e2a8,0x00000000), stub!
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:thread:SetThreadIdealProcessor (0x144): stub
fixme:thread:SetThreadIdealProcessor (0x148): stub
fixme:thread:SetThreadIdealProcessor (0x14c): stub
fixme:thread:SetThreadIdealProcessor (0x150): stub
fixme:dwmapi:DwmIsCompositionEnabled 0xc2f350
fixme:win:EnumDisplayDevicesW ((null),0,0xc2ee00,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0xc2edf8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,0xc2eda8,0x00000000), stub!
fixme:wlanapi:WlanOpenHandle (1, (nil), 0xc2f1bc, 0xc2f198) stub
fixme:wbemprox:wbem_locator_ConnectServer 0x1b35db0, L"\\\\.\\root\\cimv2", (null), (null), (null), 0x00000000, (null), (nil), 0xc2f334)
```

And it just sits at the last line until I kill the process. Any ideas?

Has anyone successfully got it running on an Atom CPU in Ubuntu 11.10 x64?

---

### Post by xamox on 2011-12-12
Does OnLive work in WINE on a standard processor?

---

### Post by achoo5000 on 2011-12-12
Yes, you can refer for example to [this thread]("http://onlivefans.com/showthread.php?7310-Running-OnLive-On-Linux-via-WINE").

OnLive has been known to run on wine for a while now, but with the problem that mouse/keyboard input isn't captured with some games because wine doesn't handle 'rawinput.' The thread talks about a hack to enable rawinput in Wine.

I, however, can not even get into the login screen let alone the menu.

---

### Post by Dlambert on 2011-12-12
I think what he's trying to say is that your CPU isn't powerful enough, or at least your configuration.

---

### Post by achoo5000 on 2011-12-12
> **Dlambert said:**
> I think what he's trying to say is that your CPU isn't powerful enough, or at least your configuration.

I see your concern. I guess in my opinion my computer should be able to display the login window regardless of how slow it is. Although I agree, getting it to run with a game will be another story.

On the other hand, when running in windows, onlive is known to work with netbooks. The whole idea is to put the hardware burden server-side.

Thanks.

---

### Post by Dlambert on 2011-12-12
Try using OpenGl in wine to render it. Or use PlayOnLinux.

---

### Post by achoo5000 on 2011-12-12
> **Dlambert said:**
> Try using OpenGl in wine to render it. Or use PlayOnLinux.

I will try opengl. One extra piece of information that I just got from an experiment using the LTS ubuntu on an USB stick. When I run it on Lucid Lynx (Ubuntu 10.04), it works, on Oneiric Ocelot (11.10) it does not. 

Any idea what that could mean?

---

### Post by Dlambert on 2011-12-13
> **achoo5000 said:**
> I will try opengl. One extra piece of information that I just got from an experiment using the LTS ubuntu on an USB stick. When I run it on Lucid Lynx (Ubuntu 10.04), it works, on Oneiric Ocelot (11.10) it does not. 

Any idea what that could mean?

Well the performance decrease from 10.04 to 10.10 (On a low end PC) are exponential in some cases. Maybe you should try Lubuntu or Xubuntu for a lighter faster distro on you limited hardware. And are you trying to run OnLive from a Usb drive? A better choice would be a full install.

---

### Post by Dlambert on 2011-12-13
Coming from the desktop effect standpoint, the Unity DE uses more 3D acceleration than GNOME2, so there's a huge change in hardware requirements. If you like UNITY, you could try UNITY 2D, the same DE without 3D acceleration, which may be good on a netbook.

---

### Post by achoo5000 on 2011-12-13
I find that the normal OS runs fine for me. And I did just try Unity2D, no luck. 

And also interestingly enough, I got it to work on a USB using Lucid, but not on my full install Oneiric.

There seems to definitely be some regression in the distro which breaks what was working on a previous distro.

---

### Post by Dlambert on 2011-12-13
> **achoo5000 said:**
> I find that the normal OS runs fine for me. And I did just try Unity2D, no luck. 

And also interestingly enough, I got it to work on a USB using Lucid, but not on my full install Oneiric.

There seems to definitely be some regression in the distro which breaks what was working on a previous distro.
Not reggesion persay, but more of increases in the hardware required.

---

### Post by achoo5000 on 2011-12-13
> **Dlambert said:**
> Not reggesion persay, but more of increases in the hardware required.

Interesting, you seem convinced that the problem is that of hardware requirements when in possession of no evidence, and even when presented with evidence to the contrary.

---

### Post by Dlambert on 2011-12-14
I'm not saying your hardware is the issue, I'm saying Ubuntu 11.10 requires more Umph to run that 10.10, and so one. Onlive may in fact be able to run on your PC just fine, just not with 11.10, at least that's what I think.

---

### Post by cdm2006 on 2011-12-23
I get this same exact problem, no screen appears and the OnLive process appears in system monitor with cpu usage at 98-100%. I can't even get it to work in virtualbox on a windows xp machine, says my system doesn't have direct3d support even though I've set the machine to use 3D acceleration. Been so desperate to get onlive to run on my netbook that I've been trying to double boot xp. Without a CD drive, its hard to install via SD card... which is what I've been attempting the past 2 days.

---

### Post by Dlambert on 2011-12-23
Install directx, and freeglut

---

### Post by gojeera on 2012-01-31
> **Dlambert said:**
> Install directx, and freeglut
install both through wine? will wine tricks work?

---

