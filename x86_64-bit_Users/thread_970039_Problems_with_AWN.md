---
title: "Problems with AWN"
date: 2008-11-03
forum: x86 64-bit Users
---

### Post by Inferno31 on 2008-11-03
Hey,
I'm new to the fourms, I've been using Ubuntu x86 since 7.04 and just recently upgraded to 8.10 from 8.04 LTS. I had some glitches (video card stopped working, and some programs and keys unresponsive) I seem to have fixed all of them but one. Awn for some reason refuses to work for me, I tried doing it through terminal, and through package manager no luck. I've posted the error message I got below when I try to install it.

> E: /var/cache/apt/archives/libawn0_0.2.6-7ubuntu1_amd64.deb: trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package libawn-bzr
E: /var/cache/apt/archives/python-awn_0.2.6-7ubuntu1_amd64.deb: trying to overwrite `/usr/lib/python2.5/site-packages/awn/awn.so', which is also in package python-libawn-bzr
E: /var/cache/apt/archives/awn-applets-c-core_0.2.6-2ubuntu4_amd64.deb: trying to overwrite `/usr/share/gconf/schemas/awn-notification-daemon.schemas', which is also in package awn-core-applets-bzr
E: /var/cache/apt/archives/awn-applets-c-extras_0.2.6-2ubuntu4_amd64.deb: trying to overwrite `/usr/share/gconf/schemas/filebrowser.schemas', which is also in package awn-core-applets-bzr


I'm fairly new to Ubuntu and terminal etc. Kind of learning as I go, any help will be greatly appreciated:D

---

### Post by Inferno31 on 2008-11-04
bump..

Any help at all would be appreciated? If this is the wrong forum can someone point me in the right direction?

---

### Post by Yellow Pasque on 2008-11-04
You have a previous install of AWN which is interfering with the new one. Do a search for 'awn' in Synaptic Package Manager and remove the -bzr packages.

---

