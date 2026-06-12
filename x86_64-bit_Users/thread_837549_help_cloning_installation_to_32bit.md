---
title: "help cloning installation to 32bit"
date: 2008-06-22
forum: x86 64-bit Users
---

### Post by rkleemann on 2008-06-22
Hi,

I have Ubuntu Hardy server installed on 64bit. I've gone through the trouble of installing and configuring a lot of things.

Now I wanted to clone this installation, but the thing is that the target server is not 64bit.

Is there some sort of program that can clone by taking all packages from the 64bit and installing the 32bit equivalents?

Thanks
Ricardo

---

### Post by cariboo on 2008-06-22
A cloned installation will not work unless you have exactly the same hardware. With different hardware different modules need to be loaded and with different modules come different configuration files.

There is a list of what is installed in /var/lib/dpkg/status. 

Maybe there is a way to parse out the file names, at least that way you have a starting point.

Jim

---

### Post by natros on 2008-06-22
use dpkg --get-selections to get a list of all packaged installed and load that list on the 32-bit system with dpkg --set-selections

---

