---
title: "Custom Kernel + Nonfree Nvidia Drivers in Kubuntu Gutsy = No Joy"
date: 2007-07-27
forum: x86 64-bit Users (Pre April '08)
---

### Post by ilikenwf on 2007-07-27
I use Kubuntu Gutsy, with a custom vanilla CK1 patched kernel on an AMD Turion 64 x2.

I have been trying to get the proprietary drivers working on my custom kernel. I have compiled the kernel module on my own, and have tried letting the nvidia installer do it too. Using either way, after editing xorg.conf I always get this when I try to load up X:

It gives some stuff about the module being built in, and then..
Fatal: Error running install command for nvidia

What gives? What should I / can I do? I do have the correct settings in the kernel (riva is off, the newer cards are on as module)... I have been trying to get this for days to no avail.

---

### Post by kidders on 2007-07-28
Hi there,

> **ilikenwf said:**
> It gives some stuff about the module being built inWhat stuff? If you've built an nvidia driver as part of your kernel, then trying to install the non-free one will make a mess.

---

### Post by stmiller on 2007-07-28
Make sure you have the proper symlink set up:

/usr/src/linux 

should point to 

/usr/src/yournewkernel.x.x

Do this:

```

$ sudo ln -sfn /usr/src/yourkernel linux

```

The nvidia installer needs this.

---

### Post by ilikenwf on 2007-07-29
> **kidders said:**
> Hi there,

What stuff? If you've built an nvidia driver as part of your kernel, then trying to install the non-free one will make a mess.


I didn't build it in ...this time...I learned from that mistake. The thing is that I just left it as it was on the default setting, as a module. I am assuming this means it built it anyway and i need to remove it and recompile...I will try that. Such is life. 

Oh...and anybody know why my doc.mk file in /usr/src/linux/debian/ruleset/targets/ would keep getting corrupted? Even when I make clean, it remains corrupted. I found a good one online that I continually have to recopy as the build process seems to corrupt it...weird...

As for the link to my source directory, I have always had that there...Thanks everyone, though!

(I know I may not appear on the forums much, but I really do know most of what I am doing...but...sometimes I do have my moments of ignorance...and that's when I come here ;) )

---

### Post by kidders on 2007-07-29
> **ilikenwf said:**
> I didn't build it in ...this time...I learned from that mistake. The thing is that I just left it as it was on the default setting, as a module. I am assuming this means it built it anyway and i need to remove it and recompile.Exactly. As a rule, you shouldn't build kernel components that might conflict with the rest of your system. Whether to compile things as modules or not depends on how you want them to perform/behave ... not on whether you want to use them.

I have no suggestions regarding your doc.mk problem though. :-( I can't say I've ever encountered any such issues. Sorry about that.

---

### Post by ilikenwf on 2007-09-16
Doc.mk is fixed, since this post I have upgraded to Gutsy, and all is well, EXCEPT that when I try to use the nvidia drivers (have tried nvidia-glx-new and nvidia-kernel-new, as well as the Nvidia installer), I get a  few X errors, including one that says that module nvidia failed to install, followed by the classic no screens error. 

The problem with this is that I have found a breakthough in kernel speed to a certain point. I have patches that I have put together from some I found on the gentoo forums, and have modded one for my own purposes. Between the new cfs patch and a patch I modded that adds a better option for timer frequency for dual-core systems, the Ubuntu kernel (yes, I patched the Ubuntu kernel) screams!

Anyway, I want to use my custom kernel, but between the nvidia drivers not working, and me not wanting to take 8-12 hours to compile the restricted modules, I don't know what to do. Is there a way to use the prebuilt restricted modules and drivers with a kernel based on the ubuntu code with different version info? I know that they would work, I just don't know how to make my custom kernel use the non-custom ubuntu modules...Yes, it can be done.

---

