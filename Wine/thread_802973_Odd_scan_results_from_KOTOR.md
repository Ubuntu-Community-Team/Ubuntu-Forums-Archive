---
title: "Odd scan results from KOTOR"
date: 2008-05-21
forum: Wine
---

### Post by GamesForLinux on 2008-05-21
I installed KOTOR under Wine with no problems, but when I started it for the first time, it scanned the system and said that it wouldn't play because I didn't have a good enough video card or processor.
My computer is from System76, and has a 8600 GT and a 2.4 Ghz dual core CPU, but the scan results came back with the following:
```
[Video]

Video Card Name=Error -- []

Video Memory=256

Desktop Resolution=800x600x32

DirectX=DirectX (9.0+) (4.09.00.0904)

OpenGL Version=2.1.2 NVIDIA 169.12

OpenGL Vendor=NVIDIA Corporation

OpenGL Renderer=GeForce 8600M GT/PCI/SSE2

Vid Card Status=Warning

GL Status=Pass

DX Status=Pass

```
```

[CPU]

CPUCount=1

CPUSpeed=800

CPUFamily=6

CPUModel=15

CPUStepping=11

CPUVendor=Intel

CPUName=Intel(R) Core(TM)2 Duo CPU T7700 @ 2.40GHz

Status=Fail

```
The second time starting it, it didn't scan, and played just fine, except it doesn't show the cursor.
My questions are:
[list=1]
[*] How do I get the cursor to show
[*] Is the CPU really only running at 800Mhz, or is this wine not reading it right?
[*] Can I edit the registry to fix the video card problem?
[/list]
I've seen the Useful Registry Keys page on the wiki, but the Direct3D folder doesn't exist in the registry, so I can't open it and change the settings inside.

---

### Post by Spectre5 on 2009-06-01
I have this same/similar problem.  My video card is not detected correctly (NVidia 9500GT with NVidia 180 driver).  Also, the sound card is not detected and thus gets a status of "warning".  This is from Kotor2 congifure.

```

[Video]

Video Card Name=Error -- []

Video Memory=64

Desktop Resolution=0x0x0

DirectX=DirectX 9.0c (4.09.00.0904)

OpenGL Version=3.0.0 NVIDIA 180.44

OpenGL Vendor=NVIDIA Corporation

OpenGL Renderer=GeForce 9500 GT/PCI/SSE2

NVidia Driver=(null)

Vid Card Status=Fail

Vid Card Driver Status=Pass

GL Status=Pass

DX Status=Pass

```

```

[Audio]

Sound Card Name=

Status=Warning

```

---

