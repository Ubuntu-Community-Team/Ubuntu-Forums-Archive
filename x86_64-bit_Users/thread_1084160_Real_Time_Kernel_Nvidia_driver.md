---
title: "Real Time Kernel Nvidia driver"
date: 2009-03-01
forum: x86 64-bit Users
---

### Post by CodyT07 on 2009-03-01
Hello, I am trying to install the Nvidia driver on my system. Ubuntu Studio Ibex 
I run Ubuntu Studio with the Real Time Kernel on a 64 bit system. I been following this guide [here](http://meandubuntu.wordpress.com/2008/07/17/install-nvidia-17713-drivers-on-realtime-kernel/)
However I ran into a snag

Here is what I done
Download the driver
Ran Command
```

sudo sh NVIDIA-Linux-x86_64-177.13-pkg2.run -x

```
Ran this command
```
 cd 
VIDIA-Linux-x86_64-177.13-pkg2
```
and from there
```
cd usr/src/nc/
```

When I go to edit *sv-linux.h*

I found __SEMAPHORE_INITIALIZER and replaced it as said, however when the guide tells me to do this

> Replace &#8220;struct semaphore&#8221; with &#8220;struct compat_semaphore&#8221;

There are many struct semaphores. Do I replaced them all or just the first one I see? Hopefully someone has had success with this. 

Reason I ask on here, their is probably a more simpler way. The Driver manager left me with bad results last time I tried, So I'm playing it safe...

---

### Post by 3Miro on 2009-03-01
I have always used the Hardware Manager and it never gave me trouble.

If you want to install the driver "the hard" way, it is probably a better idea to download from NVIDIA the 1.80 driver.

I have installed NVIDIA drivers "the hard" was several times on older linux distributions and beta drivers on newer distros and I never had trouble simply following the instructions given at the NVIDIA web-page.

---

