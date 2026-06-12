---
title: "nvidia on amd64+2.6.20+feisty no luck at all"
date: 2007-03-30
forum: x86 64-bit Users (Pre April '08)
---

### Post by durilka on 2007-03-30
I know the problems with legacy nvidia are discussed quite a lot, but so far I haven't seen exactly the same situation as mine. Hopefully using this thread I'll be able to find someone with similar issue.

The problem is after switching to feisty+2.6.20 kernels(generic and lowlatency, no custom built ones) I'm absolutely unable to use legacy nvidia drivers both via restricted modules and with nvidia installer. Everything used to work up to 2.6.17(where I have to stay) so it's not the xorg configuration problem. And when any of 2.6.20 kernels are booted computer dramatically hangs(no ctrl+alt+f1 & co, just hard reboot) even without writing the xorg.0.log so I have no information on what can go wrong and what can I submit to launchpad...

And unfortunately nv is not an option since I'm using dual head quite a lot. Actually it doesn't really work too.

Anyone? Links?

---

### Post by teaker1s on 2007-03-30
nvidia driver directly from nvidia- I've had better results this way:popcorn:

---

### Post by durilka on 2007-03-30
> **teaker1s said:**
> nvidia driver directly from nvidia- I've had better results this way:popcorn:

that's the way I'm doing it normally. after all it's same 9755 currently in repository and since the driver is binary - there's no difference on how to install...

---

