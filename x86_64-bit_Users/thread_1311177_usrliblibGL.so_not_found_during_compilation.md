---
title: "/usr/lib/libGL.so not found during compilation"
date: 2009-11-02
forum: x86 64-bit Users
---

### Post by Alex Flint on 2009-11-02
When upgrading between ubuntu releases I always lose the symlink for /usr/lib/libGL.so. I get an error like this while compiling GL-related stuff:

```
make[3]: *** No rule to make target `/usr/lib/libGL.so', needed by `libcore_lib.so'. Stop.
```

And sure enough, there is no /usr/lib/libGL.so. The libraries are all installed, though, and the solution is just:

```
sudo ln -s /usr/lib/libGL.so.185.18.36 /usr/lib/libGL.so
```

where I update the 185.18.36 each time I upgrade Ubuntu or upgrade nvidia packages by doing "ls /usr/lib/ligGL*"

I am on x64_86 and I have all the nvidia development packages installed:
```
$ dpkg -S /usr/lib/libGL.so.185.18.36
nvidia-glx-185: /usr/lib/libGL.so.185.18.36

$ dpkg -S /usr/lib/libGL.so
dpkg: /usr/lib/libGL.so not found.

$ aptitude search nvidia | grep ^i
i A nvidia-185-kernel-source        - NVIDIA binary kernel module source        
i A nvidia-185-libvdpau             - Video Decode and Presentation API for Unix
i A nvidia-185-modaliases           - Modaliases for the NVIDIA binary X.Org dri
i   nvidia-common                   - Find obsolete NVIDIA drivers              
i A nvidia-glx-185                  - NVIDIA binary Xorg driver                 
i A nvidia-glx-185-dev              - NVIDIA binary Xorg driver development file
i A nvidia-settings                 - Tool of configuring the NVIDIA graphics dr

```

So this seems like a bug to me. Can anybody enlighten me otherwise or should I report the bug?

---

