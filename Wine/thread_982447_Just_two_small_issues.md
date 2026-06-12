---
title: "Just two small issues"
date: 2008-11-14
forum: Wine
---

### Post by sonic13 on 2008-11-14
Hey guys!

First of all: I hope this will be a thread on which people answer, the last one stood empty even with a bump.

I got 'Gothic I' to work with Wine on my Ubuntu 8.10. It's patched to version 1.08k and everything works great except for two things:

1) The graphics in movie sequences is sometimes incorrect, it can look very awful. (Parts of the screen just get tesselated)

2) The sounds "flicker" somehow - sorry, I can't think of a better word.
It's not lagging, but it doesn't run through the sound fluently.
Also, the dialogue text changes to the next one right about a second before the speech finished, the end of the speech gets cut away and the next sound file is played. 
That's why I think, the sound is somehow stretched just a bit longer than it actually should be. How can I fix this?

Wine ver.: 1.1.8
Wine OS ver.: Windows XP
Library overrides: dmband.dll
                   dmcompos.dll
                   dmime.dll
                   dmloader.dll
                   dmstyle.dll
                   dmsynth.dll
                   dmusic.dll

Here's something about the hardware I use.

```
sonic@sonic-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller
00:00.6 Host bridge: VIA Technologies, Inc. Device 6290
00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 PCI bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
04:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
05:07.0 Multimedia audio controller: Ensoniq 5880B [AudioPCI] (rev 02)

```

It's hard to get the full wine output, but here's one part of it:

```
fixme:d3d7:IDirect3DVertexBufferImpl_Optimize (0x3eebc48)->(0x5038840,00000000): stub!
fixme:d3d7:IDirect3DVertexBufferImpl_Optimize (0x50396b8)->(0x5038840,00000000): stub!
fixme:d3d7:IDirect3DVertexBufferImpl_Optimize (0x4d0ffe0)->(0x5038840,00000000): stub!
fixme:d3d7:IDirect3DImpl_7_EvictManagedTextures (0x1435b0): Stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
err:d3d:IWineD3DDeviceImpl_SetupFullscreenWindow (0x148e40): Want to change the window parameters of HWND 0x10028, but another style is stored for restoration afterwards
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x1435b0)->(1,(nil)): Stub
err:ddraw:PixelFormat_WineD3DtoDD Can't translate this Pixelformat 62
err:ddraw:PixelFormat_WineD3DtoDD Can't translate this Pixelformat 63
err:ddraw:PixelFormat_WineD3DtoDD Can't translate this Pixelformat 64
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (0,0)-(640,480)
fixme:d3d7:IDirect3DVertexBufferImpl_Optimize (0x4e19048)->(0x4f220e8,00000000): stub!
fixme:d3d7:IDirect3DVertexBufferImpl_Optimize (0x4d0b668)->(0x4f220e8,00000000): stub!
fixme:d3d7:IDirect3DVertexBufferImpl_Optimize (0x4f21e98)->(0x4f220e8,00000000): stub!
fixme:d3d7:IDirect3DVertexBufferImpl_Optimize (0x4f21e70)->(0x4f220e8,00000000): stub!

```

Thank you for any help!

---

### Post by sonic13 on 2008-11-16
Just in case that someone who has the same problem will find this thread:

The solution was in my case to kill the pulseaudio process.
Good luck!

What a pity that not even in my second thread was even one response and I have to answer my own questions.

---

