---
title: "AMD64 Setup Advice?"
date: 2005-03-24
forum: x86 64-bit Users (Pre April '08)
---

### Post by mark on 2005-03-24
I'm going to put together my new desktop this weekend which will consist of:

1 - Asus A8N-SLI Deluxe mainboard
2 - AMD Athlon 64 3200+
3 - Leadtek WinFast PX6200TD PCIe display adapter

I'm migrating my drives, memory & peripherals from an Intel D865GLC-based system.  My plan is to install the latest daily image of Hoary AMD64.

My advice request: is there anything I need to look out for?  Anything "special" I need to do during the install?  Lastly (remember, this my first foray into 64-bithood, so don't laugh), I got used to installing the latest 686-SMP kernel with my Pentium 4 - is there only one kernel "flavor" for AMD64?

Thanks in advance!

Mark

---

### Post by s_p_a_r_k_y on 2005-03-25
Well my advice is as follows...use 64bit if you are willing to go without a few things working right natively.

No more windows codecs in mplayer/xine.
No flash plugins
and more...can't think of it right now.

I have mplayer and xine working in a chroot environment, where they can access 32bit windows codecs. I also have a firefox32 installed in the chroot wiht the flash plugin... So you can get things to work, but its a bitch as of now.

My friend who has an AMD64 decided to use 32bit for now until more supported programs became available. We both are using hoary, but it seems as if his 32bit hoary is more stable than my 64bit hoary (? i could be mistaken or maybe I just suck at using computers).

So if you don't want lots of messing around with things, you might want to go the 32bit way for half a year...then install 64bit. 

Just rememberto keep /home on a separate disk/partition so you can upgrade the system to 64bit without having to worry about your settings coming with it.

---

### Post by joekm on 2005-03-25
I posted something akin to this in the Warty section as well.

I just got an AMD64 based laptop and was thinking of installing the 32-bit Hoary disk when it is officially released (April 6th as I recall) and setting up a 64-bit chroot for running computationally intensive stuff like BRL-CAD, octave, z88, etc.

Seems to me that this would be the best compromise until 64-bit support has had time to mature.  This way, I get all my multi-media, flash, video card stuff working OK but still have access to the more powerful processor when I really need it.


Then again, I'm no expert....any of you more expert types care to comment?

---

### Post by mthaddon on 2005-03-25
Depends on what you're looking to do. I would suggest maybe the other way round would be a better way to go.

I'm using the AMD64 version of Hoary at the moment and have most things working nicely. Only real exceptions are RealPlayer and Flash Plugins. I am considering setting up a 32-bit chroot for this. Time is always against me in such matters...

Plus, you then have the benefit of running 64bits and of being able to contribute feedback to the furtherance of the 64 bit platform on Ubuntu. That's how I see it, anyway.

Cheers, Tom

---

### Post by wmcbrine on 2005-03-25
I don't believe it's possible to have a 64-bit chroot on a 32-bit system. Certainly the kernel, at least, must be 64-bit. Can you run a 64-bit kernel with all 32-bit libs and bins? Maybe, but I'm not gonna try it. :)

Re: kernels, there are in fact several. The default installation was "amd64-generic", and I've switched it to "amd64-k8", which is supposed to be optimized for Athlon 64, as opposed to just the common subset of Athlon 64 and Intel's version. I dunno what the differences are. There's also an Intel-optimized kernel, and an SMP version of the k8 kernel.

---

### Post by mark on 2005-03-26
My thanks to all for the replies...I see that I jumped into this on some unjustified assumptions.  I had "assumed" that I could install the 64-bit kernel/OS and still have it transparently work with 32-bit apps/libs/plugins, as necessary.  The multimedia stuff I can struggle without, except for Flash...it's become so pervasive in the Internet world that it's kinda crippling to try & work without it.

Okay, more advice/opinions.  I have no problem with having 2 separate Hoary installs - 64-bit and 32-bit, sort of a "test lab" and "production" scenario.  My immediate question is which ISO do I use for the 32-bit install?  The i386?  And should I then look for a "K8" kernel as my optimum?  And does the Athlon 64 3200+ support SMP operation, *a la* the Pentium 4/HT?  (I think it's the "later", 90nm CPU I have - although AMD doesn't make it particularly easy to find out.)

Again, thanks for everybody's patience - I didn't realize there was such a difference between AMD and Intel Linux configurations!

Mark

---

### Post by wmcbrine on 2005-03-26
[QUOTE=mark]My thanks to all for the replies...I see that I jumped into this on some unjustified assumptions.  I had "assumed" that I could install the 64-bit kernel/OS and still have it transparently work with 32-bit apps/libs/plugins, as necessary.[/quote]For the most part, it does. 64-bit apps can call 32-bit, and vice versa. It's just libraries that aren't interchangable (and plugins are a kind of library).

You can install a 32-bit Firefox (for example) to support the 32-bit plugins, without needing a whole 32-bit distro set up.

> My immediate question is which ISO do I use for the 32-bit install?  The i386?If you want to go that way, yeah.

> And should I then look for a "K8" kernel as my optimum?You mean for the i386 distro? If it's available, yeah. But it's probably not worth worrying about. A "686" or "k7" kernel will do just about as well. (A k8-optimized i386 kernel is of course quite different from an amd64 kernel complied for native 64-bit mode.)

> And does the Athlon 64 3200+ support SMP operation, *a la* the Pentium 4/HT?Have you got two (or more) processors in your system? If not, you don't need SMP.

Does Hyperthreading really equate to SMP? That doesn't sound right, but I don't keep up with Intel procs these days.

> I didn't realize there was such a difference between AMD and Intel Linux configurations!I don't think there is. The big difference is between 32-bit and 64-bit systems.

---

### Post by mark on 2005-03-27
After all the hard work...sorry for the false alarm - my D865GLC mainboard was not dead, simply suffering a case of CMOS Alzheimers.  A simple re-install of the BIOS flash image, reset the sane BIOS parameters and I'm good to go.  Fortunately, Fry's understood and took back the mainboard, CPU and display adapter I bought last weekend.

My thanks to all that chimed in on this post & I look forward to working with the 64-bit crowd in the future.

*Thanks!* 

Mark

---

