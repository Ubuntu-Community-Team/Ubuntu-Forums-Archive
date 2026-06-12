---
title: "fglrx/mesa/x.org issue on AMD64"
date: 2006-08-12
forum: x86 64-bit Users (Pre April '08)
---

### Post by usernamed on 2006-08-12
Hi,

I posted about this issue many months ago, but never did find a solution.  I'm trying to get my HP nx6125 (AMD64 laptop with ATi Radeon Xpress 200M gfx chipset) working with the proprietary ATi drivers.  I have followed the guide [here]("http://www.ubuntuforums.org/showthread.php?t=204910&highlight=GLX_SGIX_pbuffer")

but still get the following error when I run fgl_glxgears:

Using GLX_SGIX_pbuffer
Floating point exception

If I run fgl_glxgears with the -fbo option, it seems to work but I'm still getting framerates of 110-120, and I'd have expected more if I had hardware acceleration.  I'm running the latest 8.27.10_AMD64 drivers on a bog standard dapper install.  I'm no longer sure if the issue is x.org, mesa or the ati drivers.  Can anyone help?

---

### Post by Kilz on 2006-08-12
> **usernamed said:**
> Hi,

I posted about this issue many months ago, but never did find a solution.  I'm trying to get my HP nx6125 (AMD64 laptop with ATi Radeon Xpress 200M gfx chipset) working with the proprietary ATi drivers.  I have followed the guide [here]("http://www.ubuntuforums.org/showthread.php?t=204910&highlight=GLX_SGIX_pbuffer")

but still get the following error when I run fgl_glxgears:

Using GLX_SGIX_pbuffer
Floating point exception

If I run fgl_glxgears with the -fbo option, it seems to work but I'm still getting framerates of 110-120, and I'd have expected more if I had hardware acceleration.  I'm running the latest 8.27.10_AMD64 drivers on a bog standard dapper install.  I'm no longer sure if the issue is x.org, mesa or the ati drivers.  Can anyone help?

I am running a radon x200 but not an M. I get the same error on that test, and only 250-300 with the option. I think its the test you are trying.
If I use glxgears -printfps I get 3300 - 3500. I'm actually quite happy with that as its doubled over the 8.26.18 drivers.
But remember glxgears and fgl_glxgears are not benchmark applications. They are simple tests to see if the graphics are working. They also use hardware acceleration where applications for the most part use software acceleration. The x200 series are the bottom of the line, dont expect them to everything the higher priced/numbers ones do.

---

### Post by usernamed on 2006-08-12
Thanks for the response Kilz,

Maybe I am over-estimating the abilities of the product, for some reason I was expecting a little more.  It's the error that made me think something was wrong.  Is there anyone out there who had this error and fixed it?

---

### Post by Kilz on 2006-08-12
> **usernamed said:**
> Thanks for the response Kilz,

Maybe I am over-estimating the abilities of the product, for some reason I was expecting a little more.  It's the error that made me think something was wrong.  Is there anyone out there who had this error and fixed it?

You may also want to take a [look here]("http://www2.ati.com/drivers/linux/linux_8.19.10.html#176759"). This is an older release. It looks like ATI disabled something and made the -fbo required a few versions back.

---

