---
title: "Wine error getting Video memory"
date: 2008-05-12
forum: Wine
---

### Post by happysmileman on 2008-05-12
I just installed Wine-1.0-rc1 and installed Rise of Legends on it, when i start the game I get a message telling me I don't meet system requirements, if I ignore the mesage it tells me that I don't have AGP texture rendering or something enabled and performance will be affected, and then it plays the opening videos and tells me I only have 57MB graphics card and I need 64MB one, not letting me play.

Problem is, according to NVidia settings, I have a 64MB graphics card with AGP enabled.

I've tried changing registry value HKEY_CURRENT_USER\Software\Wine\Direct3D to have "VideoMemorySize" string set to "64", and it doesn't work... And if I set it any higher than 64 I get page fault errors

Oh yeah I'm running Hardy Kubuntu with KDE4, with a NVidia GeForce4 440 MX, and the restricted drivers. The game works on Windows, with a couple of graphics errors.

---

### Post by happysmileman on 2008-05-13
Bumping this since it's been a day

---

