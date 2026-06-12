---
title: "want howto AMD virtualization"
date: 2006-10-21
forum: x86 64-bit Users (Pre April '08)
---

### Post by tebibyte on 2006-10-21
Hi, I was investigating my options in getting a new PC and was wondering if anyone could tell me how to run MS vista/XP and Edgy simultaneously with **AMD virtualization**. 

I also have a few questions regarding the feature
1. can both operating systems utilize the ethernet card at the same time.
2. can you plug in an extra moniter, keyboard, mouse to access both virtual systems?

Thank you for the help.

---

### Post by kuja on 2006-10-21
I've not tried anything with hardware virtualization, however,  I know for a fact that both can access the ethernet card at the same time without issue. Not sure about the other thing either.

---

### Post by bmichel on 2006-10-22
You can't really have Today low level (hardware?) virtualization mixing Linux and Windows. If you think about something like Xen it doesn't yet fully support Windows so you can expect some issues.

If you use Linux (ubuntu) as a Host OS (main OS), you can use very easily and for free vmware player or server (I recommend the server version which comes with extra tools). Windows or other Linux/FreeBSD will be Guest OSes. Windows will work smoothly but for some 3D graphic and sound.

Also you can use Windows as an Host and Linux as a Guest. It depends of your primary OS.

Qemu, an OSS is also a solution but requires to be hands on.

If your host OS supports multi screens you should be able to split an OS on each. They will also share the network with the Guest Os having its own IP address (bridge mode), a shared IP with the Host (NAT mode) or in a private network (local) with the Host.

---

### Post by RAOF on 2006-10-23
> **bmichel said:**
> You can't really have Today low level (hardware?) virtualization mixing Linux and Windows. If you think about something like Xen it doesn't yet fully support Windows so you can expect some issues.
...

That's not actually true.  The newest Intel (merom/Core 2) and AMD processors support hardware virtualisation, and can run unmodified Windows under Xen.

That said, there was a thread in the Edgy developement forum about the Xen image (particularly the supporting tools) being slightly broken.  I'm not sure if it's fixed yet.

---

### Post by bmichel on 2006-10-23
> That's not actually true. The newest Intel (merom/Core 2) and AMD processors support hardware virtualisation, and can run unmodified Windows under Xen.

You're right, I was a little straight in my comment. The objective of XenSource is to fully support Windows but I'm not sure that you can expect something usable right now like Vmware, Qemu or Parallel. And support for AMD virtualization is still in early stage. Look at XenSource wiki:
[http://wiki.xensource.com/xenwiki/OSCompatibility](http://wiki.xensource.com/xenwiki/OSCompatibility)

If you have some weblink about a working configuration, I'll take it, I need that for my work.

---

