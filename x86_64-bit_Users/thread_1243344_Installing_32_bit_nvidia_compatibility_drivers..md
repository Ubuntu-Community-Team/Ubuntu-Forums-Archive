---
title: "Installing 32 bit nvidia compatibility drivers."
date: 2009-08-18
forum: x86 64-bit Users
---

### Post by cdysthe on 2009-08-18
Hi,

I have updated my nvidia driver to the latest version using the driver downloaded from nvidia. The instalation went fine except for when I opted for installing the 32 bit compatibility drivers (which I do need for certain apps). This is the error message from the install log:

-> Running runtime sanity check:
WARNING: The runtime configuration check failed for library
         'libGL.so.185.18.29' (expected: '/emul/ia32-linux/usr/lib/libGL.so.1',
         found: (not found)).  The most likely reason for this is that the
         library was installed to the wrong location or that your system's
         dynamic loader configuration needs to be updated.  Please check the
         32-bit OpenGL compatibility library installation prefix and/or the
         dynamic loader configuration.
WARNING: The runtime configuration check failed for library
         'libGLcore.so.185.18.29' (expected:
         '/emul/ia32-linux/usr/lib/libGLcore.so.1', found: (not found)).  The
         most likely reason for this is that the library was installed to the
         wrong location or that your system's dynamic loader configuration
         needs to be updated.  Please check the 32-bit OpenGL compatibility
         library installation prefix and/or the dynamic loader configuration.
WARNING: The runtime configuration check failed for library
         'libnvidia-tls.so.185.18.29' (expected:
         '/emul/ia32-linux/usr/lib/tls/libnvidia-tls.so.1', found: (not
         found)).  The most likely reason for this is that the library was
         installed to the wrong location or that your system's dynamic loader
         configuration needs to be updated.  Please check the 32-bit OpenGL
         compatibility library installation prefix and/or the dynamic loader
         configuration.

It seems to me the instaler puts the libs in the wrong location, but I can't figure out how to get this right. Can anyone please point me in the right direction?

---

### Post by rrfx on 2009-08-29
This may be what you need to do:

[[http://www.nvnews.net/vbulletin/showthread.php?t=137469](http://www.nvnews.net/vbulletin/showthread.php?t=137469)]("http://www.nvnews.net/vbulletin/showthread.php?t=137469")

---

