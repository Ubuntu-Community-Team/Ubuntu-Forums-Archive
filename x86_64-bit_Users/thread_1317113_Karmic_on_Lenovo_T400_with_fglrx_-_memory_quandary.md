---
title: "Karmic on Lenovo T400 with fglrx - memory quandary"
date: 2009-11-06
forum: x86 64-bit Users
---

### Post by vancouverite on 2009-11-06
I have an interesting memory problem that I haven't been able to solve.  I seem to have a large amount of memory being used that is not accounted for anywhere by programs, cache or buffers. There is a bug report open at: 

[https://bugs.launchpad.net/ubuntu/+bug/432531](https://bugs.launchpad.net/ubuntu/+bug/432531)

but it's getting no love so I thought I would put it to the community!

What happens is that my memory, particularly when using games or doing heavy browsing, climbs to very high values, often into the 1.8 GB range.  This is memory used by programs - not as cache or buffers.  The memory is retained even if I quit everything I'm doing until one of three things happens, if I standby or restart the computer it is released (obviously on the second one) or if I open ParaView ([www.paraview.org](www.paraview.org)), which I compiled from source with the -j 2 option ([link]("http://www.cmake.org/Wiki/ParaView:Build_And_Install#Build_ParaView_2")) and python scripting support, it releases *most* of it - dropping to 22%.  Totaling up all the usage in "ps aux" still only accounts for 16%.  I discovered this by accident and have no idea why this is the case.

So where could this memory be going?  How can I find it?  I have attached two screen shots, one is of /proc/meminfo when the usage is high, and the other is of /proc/meminfo after starting and quitting ParaView.  You can see that MemFree changes by 800+ MB, but none of the other values change by more than a few MB.

There is more info at the bug report in the form of outputs of ps, free and cat /proc/meminfo during high and low usage events.

Any help would be great! This is driving me nuts!

Van.

---

### Post by vancouverite on 2009-11-06
oops.  the screen shots.

---

