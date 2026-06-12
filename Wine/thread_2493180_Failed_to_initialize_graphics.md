---
title: "Failed to initialize graphics"
date: 2023-12-06
forum: Wine
---

### Post by demonenero84 on 2023-12-06
Almost all games made with unity engine used to run without problems with my wine version (wine-8.0.2). Some time ago I noticed that those game now give me a specific error ```
Failed to initialize graphics.
Make sure you have DirectX 11 installed, have up to date
drivers for your graphics card and have not disabled
3D acceleration in display settings.
InitializeEngineGraphics failed
```
After a bit of "googling" I found people with similar problems that have been told to "set the wined3d renderer to vulkan", so I did "winetricks renderer=vulkan" but I still get the same error .

This is my hardware and os
OS: Kubuntu 22.04.2 LTS x86_64
CPU: Intel i5-7400 (4) @ 3.500GHz
GPU: NVIDIA GeForce GTX 1050 (proprietary driver)

Any suggestions?
thanks a lot in advance

---

### Post by demonenero84 on 2024-01-16
Since I had a bit of free time I made a few tests.
I tried Wine-Staging same error, using open source driver same error, I finally tried installing Manjaro Linux with proprietary driver and it works :guitar:

Any suggestions to get it to work with Kubuntu?

EDIT:
removed and purged wine, installed wine staging and now everything is fine :guitar:

---

