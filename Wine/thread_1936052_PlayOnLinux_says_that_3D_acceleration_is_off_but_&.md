---
title: "PlayOnLinux says that 3D acceleration is off but &quot;glxinfo&quot; says otherwise..."
date: 2012-03-05
forum: Wine
---

### Post by PixelatedMesh on 2012-03-05
When I launch PlayOnLinux it says "You don't seem to have 3D acceleration!". Whenever I try to play a game, for example Oblivion, it lags as hell! Obviously I don't have 3D acceleration, you might think, but when I try "glxinfo | grep render" it returns that direct rendering is on. I have the NVIDIA propitiatory drivers enabled from the System Settings menu. I have also installed the appropriate drivers for my graphics card from NVIDIA's website.

I do not know what is going on, but I'm guessing that it's a compatibility error with my graphics card.

I have a NVIDIA GeForce GTX 560M graphics card.

What do I do? :confused:

---

### Post by BarfBag on 2012-03-05
I'm glad I found this topic, because I'm having the same problem.

---

### Post by knezmej on 2012-03-14
also I've the same problem as above :(

nvidia GeForce 8500 GT
the newest driver 295.20 from nvidia's website
on ubuntu 11.10 64bit

still hopefully

@PixelatedMesh, @BarfBag
Check that You have got ia32-libs and mesa-utils installed.

---

