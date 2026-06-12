---
title: "Will install DirectX help a lot?"
date: 2008-07-27
forum: Wine
---

### Post by Silpheed2K on 2008-07-27
If I want to run games that is... i have a windows partition would just tons of libraries sitting in System32... will those help Wine any?
and if so... how do I get wine to access those?
Just curious cause I really want to get game slike Dawn of War Soulstorm working on my GNU Linux

---

### Post by aoanla on 2008-07-28
> **Silpheed2K said:**
> If I want to run games that is... i have a windows partition would just tons of libraries sitting in System32... will those help Wine any?
and if so... how do I get wine to access those?
Just curious cause I really want to get game slike Dawn of War Soulstorm working on my GNU Linux

Not really. Wine has its own implementation of DirectX libraries, and installing the "original" dlls can cause more problems than it might fix. Unless you really know what you're doing, I'd say it's not worth it.

---

### Post by gjoellee on 2008-07-28
if you want to play games with WINE it should be something that supports OpenGl ex:
Counter Strike and WoW

---

### Post by aoanla on 2008-07-28
> **gjoellee said:**
> if you want to play games with WINE it should be something that supports OpenGl ex:
Counter Strike and WoW

Not at all. Source engine games work fine in Wine, and they don't do native OpenGL.
Wine's DirectX implementation transparently maps Direct3D calls onto OpenGL calls, and does it pretty well (although DirectX 9 support is still a bit slow for some games, and DirectX 10 just doesn't work).

---

