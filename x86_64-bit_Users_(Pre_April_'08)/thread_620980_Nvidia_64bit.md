---
title: "Nvidia 64bit"
date: 2007-11-23
forum: x86 64-bit Users (Pre April '08)
---

### Post by thpmachina on 2007-11-23
Hi, sorry this may have been posted before but tbh i just can't often get anything useful out of the forum search...all i'm wondering is, are the restricted Nvidia drivers that Gutsy notifies you about on first start in the 64 bit version the **64 bit drivers** made available by Nvidia?

Cheers all.

---

### Post by PmDematagoda on 2007-11-23
Yes they are, otherwise they would require more work than would be really needed, have more problems than the normal 64 bit one, or be totally unusable on 64 bit. So there is no doubt that the 64 bit version of the Nvidia driver is installed when you use the Restricted Drivers Manager on Ubuntu x64.

---

### Post by John.Michael.Kane on 2007-11-23
This may be of help. This where nvidia-glx files where installed.As you can see nvidia makes use of /usr/lib32/.Which might mean the binary is 32bit.

```
/.
/usr
/usr/bin
/usr/bin/nvidia-bug-report.sh
/usr/bin/nvidia-settings
/usr/bin/nvidia-xconfig
/usr/lib
/usr/lib/xorg
/usr/lib/xorg/modules
/usr/lib/xorg/modules/drivers
/usr/lib/xorg/modules/drivers/nvidia_drv.so
/usr/lib/xorg/modules/extensions
/usr/lib/xorg/modules/libglx.so.1.0.9639
/usr/lib/tls
/usr/lib/tls/libnvidia-tls.so.1.0.9639
/usr/lib/nvidia
/usr/lib/nvidia/tls_test
/usr/lib/nvidia/tls_test_dso.so
/usr/lib/libXvMCNVIDIA.so.1.0.9639
/usr/lib/libGL.so.1.0.9639
/usr/lib/libGLcore.so.1.0.9639
/usr/lib/libnvidia-cfg.so.1.0.9639
/usr/lib/libnvidia-tls.so.1.0.9639
/usr/sbin
/usr/sbin/nvidia-glx-config
/usr/share
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/nvidia-settings.1.gz
/usr/share/man/man1/nvidia-xconfig.1.gz
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/nvidia-glx
/usr/share/bug
/usr/share/bug/nvidia-glx
/usr/share/bug/nvidia-glx/script
/usr/share/doc
/usr/share/doc/nvidia-glx
/usr/share/doc/nvidia-glx/README.txt.gz
/usr/share/doc/nvidia-glx/nvidia-settings-user-guide.txt
/usr/share/doc/nvidia-glx/README.Debian
/usr/share/doc/nvidia-glx/copyright
/usr/share/doc/nvidia-glx/examples
/usr/share/doc/nvidia-glx/examples/XF86Config.sample.gz
/usr/share/doc/nvidia-glx/changelog.Debian.gz
/usr/share/doc/nvidia-glx/NVIDIA_Changelog.gz
/usr/lib32
/usr/lib32/nvidia
/usr/lib32/libGL.so.1.0.9639
/usr/lib32/libGLcore.so.1.0.9639
/usr/lib32/libnvidia-cfg.so.1.0.9639
/usr/lib32/libnvidia-tls.so.1.0.9639
/usr/lib32/tls
/usr/lib32/tls/libnvidia-tls.so.1.0.9639
/usr/lib/xorg/modules/libglx.so
/usr/lib/tls/libnvidia-tls.so.1
/usr/lib/libXvMCNVIDIA_dynamic.so.1
/usr/lib/libXvMCNVIDIA.so.1
/usr/lib/libnvidia-tls.so.1
/usr/lib/libnvidia-cfg.so.1
/usr/lib/libGLcore.so.1
/usr/lib/libGL.so.1
/usr/lib32/tls/libnvidia-tls.so.1
/usr/lib32/libnvidia-tls.so.1
/usr/lib32/libnvidia-cfg.so.1
/usr/lib32/libGLcore.so.1
/usr/lib32/libGL.so.1
```

Note: on further looking it would seem there is a 64bit deb [http://packages.ubuntu.com/gutsy/misc/nvidia-glx-new](http://packages.ubuntu.com/gutsy/misc/nvidia-glx-new) as to why it installs files in /usr/lib32 is unknown to me.

---

### Post by Arkainium on 2007-11-23
I don't think that means the driver is 32-bit.  It makes use of /usr/lib32 because it needs to provide OpenGL to both 64-bit and 32-bit binaries.  The driver itself goes into /usr/lib/xorg/... which is built for 64-bit.

---

### Post by John.Michael.Kane on 2007-11-23
> **Arkainium said:**
> I don't think that means the driver is 32-bit.  It makes use of /usr/lib32 because it needs to provide OpenGL to both 64-bit and 32-bit binaries.  The driver itself goes into /usr/lib/xorg/... which is built for 64-bit.

I did say it "might" as i was not sure. That said I can understand where you going with what you are saying.

---

### Post by grossaffe on 2008-03-06
does anyone else have a problem of not being able to install the nVidia restricted drivers?  i get a message:
 "The software source for the package

   nvidia-glx-new

 is not enabled."

---

### Post by CWaugh on 2008-03-06
> **grossaffe said:**
> does anyone else have a problem of not being able to install the nVidia restricted drivers?  i get a message:
 "The software source for the package

   nvidia-glx-new

 is not enabled."

I got that message before I was able to get internet access, which was also caused by a restricted driver.

---

