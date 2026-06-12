---
title: "Firefox crashes on Digg.com"
date: 2008-04-23
forum: x86 64-bit Users
---

### Post by cdean on 2008-04-23
Every time I visit Digg.com, Firefox crashes. It seems unrelated to flashplugin-nonfree and nspluginwrapper, but it could be.

When I run Firefox in a terminal, I get a simple Segmentation Fault.

My gdb-fu is pretty weak--anyone else having this problem and can debug it?

I'm on Hardy RC amd64.

---

### Post by movieman on 2008-04-23
64-bit Firefox seems to have problems in general; I haven't tried 64-bit Firefox on Ubuntu, but I have two CentOS machines running it and on one Firefox will just randomly exit for no reason (with no error message) and on the other it will crash on visiting certain sites like honda.ca... the latter, I think, is a Flash crash.

Haven't seen any similar problems with 32-bit Firefox.

---

### Post by cdean on 2008-04-23
I've been using 64-bit Firefox since Gutsy and didn't ever have problem with it, save with nspluginwrapper when it was broken for a few days.

Honestly, I don't think the problem is Flash-related. I can't reproduce the behavior on any other Flash-heavy site. I'm almost thinking that the problem is in Javascript--Digg uses it waaay too much and it slows every browser down, IMO.

---

