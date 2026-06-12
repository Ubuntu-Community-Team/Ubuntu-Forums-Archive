---
title: "32-bit version of GStreamer packages on 64-bit Ubuntu"
date: 2013-04-08
forum: Wine
---

### Post by temmokan on 2013-04-08
I am trying to have System Shock 2 run on Ubuntu 12.04 64-bit. It has soon become obvious it can't live with 64-bit default arch, so I tried to switch to 32-bit Wine prefix.

The problem is I couldn't install 32-bit versions of GStreamer packages to handle no sound/WSOD issues. When I tried to force installing :i386 versions, the Aptitude started with wiping 64-bit versions and all the dependent packages. That's not appropriate, I do not like to have a chimera state of system with 32-bit and 64-bit packages intertwined - Azathoth only knows what happens at the next update.

Is it known whether there's a simple way (other than recompile everything manually and then try to explain Wine where to take the libraries) to install 32-bit GStreamer packages without switching back to 32-bit OS and/or creating the mentioned chimera?

Thanks in advance.

---

