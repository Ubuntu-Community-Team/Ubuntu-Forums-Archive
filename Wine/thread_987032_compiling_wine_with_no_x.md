---
title: "compiling wine with no x"
date: 2008-11-19
forum: Wine
---

### Post by JohnLM_the_Ghost on 2008-11-19
First thing! Is it actually possible to compile wine not requiring Xserver?

Basically my point is to run few Windows apps on a debian server. Thing is... I'm not interested what those programs output, I just need them running. Server currently hasn't xserver, and I'm not looking forward to change that.

I suppose there are also other tricks to do that... like xvfb?

p.s. One of windows programs is backburner server, which is capable to output in cmd. It wouldn't hurt seeing the output in terminal, but that ain't mandatory.

---

### Post by Dizzle7677 on 2008-11-19
./configure --help from the wine source directory should give you a few options.

---

