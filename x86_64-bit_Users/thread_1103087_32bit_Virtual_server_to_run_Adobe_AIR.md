---
title: "32bit Virtual server to run Adobe AIR"
date: 2009-03-22
forum: x86 64-bit Users
---

### Post by lduperval on 2009-03-22
Hi,

In an effort to get Adobe AIR to work correctly on my machine, I am considering the possibility of running and installing it in a 32bit virtual server (VMWare, KVM, or other).

Why? Because when I follow the instructions in the pinned thread above, as well as the ones on the Adobe site, it a) doesn't work, I can't install and b) makes my system unstable: networking fails, I get system hangs when using Java, etc.

Can anyone point me to a good location for creating a 32bit virtual server that would allow me to install and run Air?

Thanks,

L

---

### Post by Vadi on 2009-03-22
Virtualbox is probably the easiest way to go about it: [http://www.virtualbox.org/](http://www.virtualbox.org/)

Then you can download a 32bit Ubuntu and install within it.

Though, I do have air working fine on my 64bit machine (but I did not follow those instructions. Just ran the .bin and that's it)

---

### Post by lduperval on 2009-03-22
Hmmm.. Are you on Intel 64 or AMD 64? I'm on the latter. I don't know if that makes a difference or not.

Thanks for the virtualbox link, I'll take a look.

L

---

### Post by Vadi on 2009-03-22
It shouldn't make a difference, but I am on an intel cpu

---

### Post by lduperval on 2009-03-22
Maybe it does, as I am on AMD. Or, I have another package that conflicts with the intallation procedures.

One very visible problem is that once I install the files from the .deb packages for Adobe Air on my system, networking fails (on top of the CLASS64 problem I allude to in the pinned thread above). The only way to fix it is to remove the files /usr/lib32 and reinstall the libssl3, libnss3 and libsmime 64bit libraries.

I am in the process of installing 8.10 on a virtual box, we'll see what happens.

L

---

