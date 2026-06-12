---
title: "Wine and Rift"
date: 2011-07-17
forum: Wine
---

### Post by Sunfist on 2011-07-17
I got Rift installed with no major problems, but every time I start the game a message comes up saying I need to install Directx 9. I thought some type of directx emulation was built into Wine. Was wondering if I really need to try to install directx or at the least is there a way to get that warning to go away.

---

### Post by Kenjitamura on 2011-07-21
Just to be sure you need to be using the wine developmental version 1.3.22 or earlier with winetricks installed.  If you use 1.3.23 or 1.3.24 you're going to be in for really glitchy graphics that the changes to d3dx9 brought.  Run the commands > winetricks d3dx9 and > winetricks vcrun2008  Go into winecfg and under the Libraries tab scroll down the overrides to *d3dx9_43 edit it and change it to builtin.

---

