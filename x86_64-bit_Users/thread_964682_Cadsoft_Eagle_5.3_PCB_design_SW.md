---
title: "Cadsoft Eagle 5.3 PCB design S/W"
date: 2008-10-31
forum: x86 64-bit Users
---

### Post by Richard-g8jvm on 2008-10-31
Hi

It would appear that Cadsofts Eagle software in far from compatible with
with the AMD 64 bit versions 8.04 and 8.10.
It was only working for a while when I changed distros and moved the Eagle directory which was built on MDV2008 with my home dir.

On a clean install of both 8.04 and 8.10 the installer borks.
First it cant create its temp directory in /tmp.

You have to create the whole path in /tmp for it.
After that it fails on finding libXrender as it runs in 32 bit mode, and when a symlink is put in to point to libXrender it borks with wrong elf class.

The only way I've found to use it on this machine is to put in a second HD and load MDV on it and Eagle installs and prints OK from that.

BTW unplug the HD with Ubuntu on it if installing Mandriva 2008 or 2009
as trashes the mbr  and /boot on the primary HD


Richard

---

