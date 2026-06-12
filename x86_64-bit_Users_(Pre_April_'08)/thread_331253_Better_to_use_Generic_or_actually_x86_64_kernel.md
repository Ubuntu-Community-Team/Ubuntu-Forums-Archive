---
title: "Better to use Generic or actually x86_64 kernel"
date: 2007-01-04
forum: x86 64-bit Users (Pre April '08)
---

### Post by Elvish Legion on 2007-01-04
In your opinion is it better to use the generic kernel or use the one built for 64bit processors?


Edit: Just noticed they are now no longer needed thanks to generic, solves my question

---

### Post by kidders on 2007-01-04
Hi there,

Naturally, it's best to use the correct kernel build for your architecture. By "generic", I imagine you mean vanilla kernels, straight from kernel.org, which is a separate issue really, imo.

---

### Post by Elvish Legion on 2007-01-04
Whats wrong with the vanilla kernels? And what kernel would you recommend? I like to use things from the repos if possible to make managing updates a little easier

---

### Post by kidders on 2007-01-04
Hey again,

All Linux kernels are based on the basic vanilla kernel, so there's nothing at all wrong with it per se. For a variety of reasons, it's often best to stick with the versions provided by Ubuntu though (unless of course, you have a specific reason not to), since they may have been patched, or otherwise tweaked, to work better with the rest of a Ubuntu system. In either case, the architecture a kernel is built for is an entirely separate issue.

I seem to have misunderstood your o/p. It looked as though you were wondering what the impact of using a kernel compiled for a CPU architecture you don't have would be, so I just wanted to remark that, clearly, you shouldn't. Oops. :-?

---

### Post by BIGtrouble77 on 2007-01-05
If you are running a 64bit kernel I don't think it really matters whether you use the generic kernel vs. k8/server/xeon kernel.  It matters much more if you are running the i386 32bit kernel because that one is severely limited to provide compatibility with a wide variety of hardware.

If you run a 64bit kernel then you will probably get minimal performance improvements with more custom kernel builds.  I think we're pretty much at a point of diminishing returns when you talk about modern hardware.  Older hardware can have noticable improvements with custom builds, but someone who has a 3ghz Dual Core athlon won't see much of anything.  If you didn't know the generic kernel now supports SMP.

So I would just go with the generic kernel (which is what I use). Custom building your own will cause some problems.  I have a custom kernel build for real-time audio apps, but some things (like drive mounting) don't work properly.  On top of that, you may have issues with video drivers from the repos if the restricted modules aren't compatible with your kernel (for nvidia users).

Edit: lol, I just noted the poster's edit.

---

### Post by MetalMusicAddict on 2007-01-05
Funny thing. Whether you run the 32bit or 64bit -generic kernel from the repos your running the same kernel.

---

