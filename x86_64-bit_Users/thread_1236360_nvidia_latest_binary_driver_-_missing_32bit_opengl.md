---
title: "nvidia latest binary driver - missing 32bit opengl support"
date: 2009-08-10
forum: x86 64-bit Users
---

### Post by interzoneuk on 2009-08-10
Hi.

I am installing the latest binary driver ( NVIDIA-Linux-x86_64-185.18.31-pkg0.run ) in Jaunty AMD64.

The driver installs fine but misses the option to install 32bit opengl support.

In other distros this occurs if I am missing a certain 32bit package.

Anyone know what package I should install to get the 32bit option.

Regards

---

### Post by n3had on 2009-08-10
> **interzoneuk said:**
> Hi.

I am installing the latest binary driver ( NVIDIA-Linux-x86_64-185.18.31-pkg0.run ) in Jaunty AMD64.

The driver installs fine but misses the option to install 32bit opengl support.

In other distros this occurs if I am missing a certain 32bit package.

Anyone know what package I should install to get the 32bit option.

Regards

**NVIDIA-Linux-x86_64-185.18.31-pkg2.run**

---

### Post by interzoneuk on 2009-08-13
Thanks for that.

It was all my fault ... I was using the driver downloaded via abs in Arch linux - Arch linux separates the 64 and 32 bit packages - explaining why it missed the 32bit section.

Thanks for your amazingly quick response.

Cheers

---

