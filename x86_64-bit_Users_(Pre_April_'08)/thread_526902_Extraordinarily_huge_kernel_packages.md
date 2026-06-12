---
title: "Extraordinarily huge kernel packages"
date: 2007-08-16
forum: x86 64-bit Users (Pre April '08)
---

### Post by mokomull on 2007-08-16
I'm trying to build a kernel package with a fix for my sound card, outlined on my blog at [http://blog.mmlx.us/2007/08/ubuntu-and-my-d630.html]("http://blog.mmlx.us/2007/08/ubuntu-and-my-d630.html").  I have a kernel package, and it works beautifully.  The only problem is that it's *huge*.  It's about 80MB in .deb format, expanding to over 250MB of kernel modules.  I based my .config around the stock Ubuntu kernel options, because even though I've been compiling kernels for quite some time, I always end up leaving something important out, and I want to maintain the feel of "just plug it in" to get new devices working.  How does the Ubuntu team get their packages so small?

---

### Post by ddrichardson on 2007-08-17
Are you making a compressed kernel?

---

