---
title: "Lid switch only works once..."
date: 2007-07-18
forum: x86 64-bit Users (Pre April '08)
---

### Post by firecat53 on 2007-07-18
My lid switch only works once to suspend my laptop. Then it has to be manually suspended (fn F6 or from menu) after that until the next reboot. Using the suspend2 patch and uswsusp. (haven't got hibernate working yet :( )

HP dv6000 series amd64 with 2.6.21 kernel (compiled). 

Any thoughts? I'm not even sure where to start troubleshooting.

Thanks!

Scott

---

### Post by sel on 2007-07-18
It's a bug with the latest HAL causing issues with suspend in general (basically the second suspend fails).

Some people have regressed to the previous HAL to fix this bug. You can do this by:

1. open synaptic package manager
2. search for 'hardware abstraction'
3. highlight 'hal'
4. Press [Ctrl]+[E]
5. this will pop a dialogue up allowing you to select he previous version of the HAL (version 5.8.1-4ubuntu12)
6. Click he 'Force Version' button
7. Ignore anything like 'Sorry David I'm afraid I can't do that'

You'll then have to ignore automated updates for the HAL 0.5.9.1ubuntu2~feisty1until they offer a fixed version.

---

### Post by firecat53 on 2007-07-18
Hmmm...the machine still suspends fine (to ram, at least) after the first time, using either the menu or the fn-F6. It's just the lid switch that doesn't work. But I'll give it a try. Thanks!  :)

Scott

---

